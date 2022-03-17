## **Styles**

For the moment we can't apply something like XAML Styles, anyway, using Styles it's a good practice to reuse views. A good aproximation to create Styles is using ExtensionMethods

```
[Body]
View body() => new VStack(spacing:20)
{
    //Header
    new Text("My new MAUI MVU app)
        .HeaderStyleText();
    
    new Text("One caption")
        .NormalStyleText();

    new Text("Another caption")
        .NormalStyleText();

    new Text("Subtitle")
        .NormalStyleText();
            
}

//In another class

public static class StyleExtensionsMethods
{
    public static Text HeaderStyleText(this Text text)
        => text.FontWeight(FontWeight.Bold)
            .Color(Color.Blue);

    public static Text NormalStyleText(this Text text)
        => text.FontWeight(FontWeight.Light)
            .Color(Color.Gray);
}

```


Comet has a style system using a StyleId property, there are default styles located inside *EnviromentKeys.*View.Style.*DiferentsStyles* i.e. *Enviroment.Text.Style.H6*

You can change defined styles using SetEnviroment method creating a inherited Style class, check this [file](https://github.com/dotnet/Comet/blob/fbb8bddb7e8fb356ab7b7f1a3e36a6a6e4366166/src/Comet/Styles/Material/MaterialStyle.cs) for a good sample.