## MVVM application to MVU application

We talk about a common scenario that receive when arrive MAUI. Stable Xamarin.Forms application created with MVVM architecture that migrate to MAUI. 

First thought that we have, it's destroy all application, create a new project a starts to works in MVU. However it's a bad solution, we lost a lot of work, all business logic (Services in MVVM) that are check and evaluated in the past. Also must be a good candidate to reuse. (Pure functions, tests, etc). 

The common mistake that takes when start from scratch is take account the old project, copy and paste almost literally a lot of parts of code and then you would take the same mistakes that you takes in the past.

A common MVVM Xamarin Forms app structure are:


- App
    - Model
    - Locator | IOC
    - Messenger Service
        - Services
        - Views
            - Behaviors
            - Converters
            - Views (Pages)
            - Controls | Renders
            - Styles
            - Effects
        - ViewModels
            - Commands            
    - Unit Tests
        - Services Tests
        - ViewModels Tests
    - UI Tests (Maybe)


A common MVU app structure are: (Taken Elm sample architecture)

- App 
    - Data
        - Services
        - Models related with services
    - Domain
        - Base
            - Commands            
        - Models related with states
    - Views
        - IView (Interface for every view)
        - View
    - Update 
        - Messages
        - Command