# Introduction

For the moment MAUI support MVVM, RxUI and MVU arquitecture. However, I think the real good perfomance related with MAUI is using MVU.

For the moment Microsoft gives real support to Comet: https://github.com/dotnet/Comet

Related with MVU architecture, at equals happens with another architecture, there are concerns related with this implementation: https://github.com/dotnet/maui/issues/118

It's true, Fabolous (https://github.com/fsprojects/Fabulous) have a real MVU implementation instead of Comet. But, IMO, Comet tries brings to MVVM developers (and Xamain devs) a friendly way to implement a MVU architecture. It's a new paradigm, all Xamarin devs and all .NET devs has inserted MVVM architecture in our ADN, so trying to change this, requires a lot of work.

MVU brings a lot of improvements such as:

- Unidirectional binding system that allows:
    - A better understanding to handle states.
    - Less bugs
    - Better perfomance

- Near functional paradigm instead POO paradigm
    - Because State concept trying to get readonly (inmmutable) elements
    - We search only pure functions

- Good opportunity to create Atomic design
    - https://atomicdesign.bradfrost.com/chapter-2/
    - The way to create views helps to think in Atoms (view parts) more than organisms (page)
        - When you develop with MVVM paradigm and create a new page, you start to thinking in design a Page
        - When you develop with MVU paradigm and create a new page, you start to thinking in design a Page, however all the view parts are separate and helps to create small parts (atoms)