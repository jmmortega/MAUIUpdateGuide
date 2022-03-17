# Layouts

We have a good point here, if you take a look inside of MAUI source code, you can check there a two Layouts folders:

- [LegacyLayouts](https://github.com/dotnet/maui/tree/a5d5137f61b736534b48e7a2233db72b05b5a2a8/src/Controls/src/Core/LegacyLayouts)
    - Include al Forms layouts that all we know
- [Layouts](https://github.com/dotnet/maui/tree/a5d5137f61b736534b48e7a2233db72b05b5a2a8/src/Controls/src/Core/Layout)
    - Include new versions of layouts near that we know from Forms.

For the moment in the MAUI preview 11, there any notice related which how plans related with legacy layouts, in first moment seems we don't have any problem with common layouts such as [Grid],[StackLayout], [FlexLayout] and [AbsoluteLayout] because there a implementation inside of MAUI layouts, in other hand, I start to thinking how to do with legacy ones that in this case is **RelativeLayout**.

Anyway, I start to look how implements the new legacy system, because it's pretty sure there are things that change [like remove *AndExpand* suffix from Vertical|Horizontal options](https://github.com/dotnet/maui/pull/3362)

## Where is my ForceLayout method?

A method that I called in Forms often times was **ForceLayout** this method dissapear. So the question it's. How force refresh for a Layout? Short answer is, you don't needed, in Forms, when Add a new element inside of a layout, should be situations that invalidation of view, can't provoke

Anyway, if you need provoke refresh inside of a Layout, I think the best way to to provoke invalidation maybe is use [InvalidateMeasureNonVirtual](https://github.com/dotnet/maui/blob/1cd6ed9e1736f074aa3340c48e5a7913bd77c841/src/Controls/src/Core/VisualElement.cs#L853) for default use EditorBrowsable(EditorBrowsableState.Never) attribute, more common in Forms to avoid appear in documentation. So in my experience related with EditorBrowsable(EditorBrowsableState.Never) attributes means *"you could use it, but, take care because it's for internal use"* this method receive an **InvalidationTrigger** enum, to mark why invalidate your View.