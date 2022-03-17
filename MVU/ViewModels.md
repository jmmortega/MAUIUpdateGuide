
## **ViewModels**

We need to change mentality related how manage state, when talking about MVU and MAUI. We can remove
ViewModels for Commands and Messages entities, that our part of Update.

It's difficult to think when start, however, when change the paradigm mentality it's very easy to achieve.

### **Scenario 1**

Think in a list that allow selection and can be empty. We identify three states of a view:
- Select
- Empty
- Readonly

So in this case our view should be work in three ways. With a viewmodel perspective we have several booleans to mark different states and modify how it's works changing state.

In a MVU architecture we need to control this three states and view draws with this state changes.


### **Scenario 2**

We have a form that open in readonly and editing mode. In this scenario, we have two states to manage:

- Readonly
- Edition

One more time, in a ViewModel architecture we have booleans that control this states and change the view.

With a MVU architecture we need draw the view using take account this states.

*Note: We create a repository to try to explain with code this scenarios*

### **Commands and Messages**

The way to communicate changes inside of view it's using Command and Messages, when using MVVM, IMO, Commands has a few responsability that should have, in any case, in a MVU perspective, commands have more responsability and good explanation related with how communicate changes we locate in this [Fabulous documentation](https://fsprojects.github.io/Fabulous/Fabulous.XamarinForms/update.html) samples it's writen in F# but reflects the idea that how must be works this communication.

**In conclusion**, we need small chunks of view, because we control small easy types of state. We need to start to avoid think in a screens, to start to think in states and how works inside of our views.