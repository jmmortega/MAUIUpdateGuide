## **Views**

XAML views dissapear and now write in C# code. (Like a old Xamarin Forms)

**Tips and concerns**

*Common sense and clean code, please*

- Think in atom design
    - Normal page in XAML have a lot of lines
    - Reduce methods for view

We should avoid
```
        [State]
		readonly CreditCard Card;

		readonly State<bool> remember = false;

		public DemoCreditCardView3()
		{
			Card = new CreditCard();
		}


		[Body]
		View body() => new VStack(spacing: 20)
		{
			new VStack()
			{
				new VStack()
				{
					new ShapeView(new RoundedRectangle(4.0f)
						.Style(Graphics.DrawingStyle.Fill)
						.Fill(Colors.Grey))
						.Frame(40,30,alignment: Alignment.Trailing)
						.Margin(top: 30, right: 30)
						.FitHorizontal(),

					new Text("CARD NUMBER")
						.FontSize(10)
						.Color(Colors.Silver)
						.Margin(left: 30),

					new Text(Card.Number)
						.FontSize(14)
						.Color(Colors.Black)
						.Margin(left: 30, bottom:20)
						.Frame(height:20),

					new HStack()
					{
						 new Text("EXPIRATION")
							.FontSize(10)
							.Color(Colors.Silver)
							.Frame(width: 200),

						 new Text("CVV")
							.FontSize(10)
							.Color(Colors.Silver),
					}.Margin(left:30),

					new HStack()
					{
						new Text(Card.Expiration)
							.FontSize(14)
							.Color(Colors.Black)
							.Frame(width: 200),

						new Text(Card.CVV)
							.FontSize(14)
							.Color(Colors.Black)
					}.Margin(left:30, bottom:30).Frame(height: 20),

				}.RoundedBorder(radius: 8, color: "#3177CB", filled: true).Margin(30)
			}.Background("#f6f6f6"),

			new BorderedEntry(Card.Number,"Enter CC Number", "\uf09d")
				.Margin(left:20, right: 20),

			new HStack(spacing:20)
			{
				new BorderedEntry(Card.Expiration, "MM/YYYY", "\uf783")
					.Frame(height: 40, width: 200)
					.Margin(left:20),

				new Spacer(),

				new BorderedEntry(Card.CVV, "CVV", "\uf023")
					.Frame( height: 40, width: 100)
					.Margin(right:20),
			},

			new HStack
			{
				new Toggle(remember),
				new Text("  Remember Me")
			}.Margin(left:20),

			new Button("Purchase for $200")
				.RoundedBorder(22, Colors.SlateGrey)
				.Background(Colors.SlateGrey)
				.Color(Colors.White)
				.Frame(height:44)
				.Margin(left:20, right:20),

			new Separator(),

			new Button("Or Pay with PayPal")
				.RoundedBorder(22, Colors.SlateGrey)
				.Color(Colors.SlateGrey)
				.Frame(height: 44)
				.Margin(left:20, right:20),


		}.FillHorizontal().Frame(alignment: Alignment.Top);

        //Rest of code...

```

**Taken from Comet samples [CreditCardView3.cs](https://github.com/dotnet/Comet/blob/dev/sample/Comet.Samples/Views/DemoCreditCardView3.cs) (Remember it's a sample not real code ¬¬)

Sounds better...

```
        
		[State]
		readonly CreditCard Card;

		readonly State<bool> remember = false;

		public DemoCreditCardView3()
		{
			Card = new CreditCard();
		}


		[Body]
		View body() => new VStack(spacing: 20)
		{
			new VStack()
			{
				CardInformation()
			}.Background("#f6f6f6"),

			new BorderedEntry(Card.Number,"Enter CC Number", "\uf09d")
				.Margin(left:20, right: 20),

			NewCardEntry(),
			
			PaidActions()
	
		}.FillHorizontal().Frame(alignment: Alignment.Top);

		private IView CardInformation()
		    => new VStack() {
				new ShapeView(new RoundedRectangle(4.0f)
						.Style(Graphics.DrawingStyle.Fill)
						.Fill(Colors.Grey))
					.Frame(40, 30, alignment: Alignment.Trailing)
					.Margin(top: 30, right: 30)
					.FitHorizontal(),

				NewCardNumberEntry(),
				NewCardExpirationCVVEntry(),

				ExpirationAndCVVLiterals(),
				ExpirationAndCVVData(),
				
		}.RoundedBorder(radius: 8, color: "#3177CB", filled: true).Margin(30);

		private IView NewCardNumberEntry()
                    => new VStack {
				new Text("CARD NUMBER")
					.FontSize(10)
					.Color(Colors.Silver)
					.Margin(left: 30),

				new Text(Card.Number)
					.FontSize(14)
					.Color(Colors.Black)
					.Margin(left: 30, bottom: 20)
					.Frame(height: 20)
			};
			

		private IView NewCardExpirationCVVEntry()
			=> new HStack(spacing: 20) {
				new BorderedEntry(Card.Expiration, "MM/YYYY", "\uf783")
					.Frame(height: 40, width: 200)
					.Margin(left: 20),

				new Spacer(),

				new BorderedEntry(Card.CVV, "CVV", "\uf023")
					.Frame(height: 40, width: 100)
					.Margin(right: 20),
			};
		
		private IView ExpirationAndCVVLiterals()
			=> new HStack() {
				new Text("EXPIRATION")
					.FontSize(10)
					.Color(Colors.Silver)
					.Frame(width: 200),

				new Text("CVV")
					.FontSize(10)
					.Color(Colors.Silver),
			}.Margin(left: 30);

		private IView ExpirationAndCVVData()
			=> new HStack() {
				new Text(Card.Expiration)
					.FontSize(14)
					.Color(Colors.Black)
					.Frame(width: 200),

				new Text(Card.CVV)
					.FontSize(14)
					.Color(Colors.Black)
			}.Margin(left: 30, bottom: 30).Frame(height: 20);
		
		private IView PaidActions()
			=> new HStack {
				new Toggle(remember),
				new Text("  Remember Me"),


				new Button("Purchase for $200")
				.RoundedBorder(22, Colors.SlateGrey)
				.Background(Colors.SlateGrey)
				.Color(Colors.White)
				.Frame(height:44)
				.Margin(left:20, right: 20),

				new Separator(),

				new Button("Or Pay with PayPal")
					.RoundedBorder(22, Colors.SlateGrey)
					.Color(Colors.SlateGrey)
					.Frame(height: 44)
					.Margin(left: 20, right: 20)
			}.Margin(left: 20);
```
    
Maybe you think, *"ok, it's a hit the target situation"* however the next step it's move to different classes and try to think in atomic design, create small pieces of views and then think in states more simple. Remember you create a production code, that should be more maintable possible.
