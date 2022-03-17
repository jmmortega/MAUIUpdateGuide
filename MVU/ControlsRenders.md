## **Controls | Renderers**

There are several considerations to take account:
- Basic inherit for controls should be View, if you create a Container you should inherit from ContainerView
- All BindableProperties in your controls should be Binding\<Type> 
    - **Remember** only for values that can change the state!    
- For values that can't change the state use a simple value

### **For renderers**

If renderer it's really complex and you don't want rewrite you can migrate using [MAUI compatibility](https://javiersuarezruiz.wordpress.com/2021/07/19/net-maui-compatibility-reutilizar-tus-renderers-sin-cambios/)

If you want rewrite you can need use [handlers](https://javiersuarezruiz.wordpress.com/2021/07/19/portear-un-custom-renderer-de-xamarin-forms-a-un-custom-handler-de-net-maui/)