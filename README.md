# winui3-photo-viewer

Start with the Step here:

https://learn.microsoft.com/en-us/windows/apps/get-started/simple-photo-viewer-winui3?tabs=cs



# Review Layout

* RelativePanel, 
* StackPanel, 
* Grid, 
* VariableSizedWrapGrid, and 
* Canvas. 

## Panel Attached Properties

Attached Properties allows child elements to inform parent elements how they should be positioned.

e.g. in the following case, the button has an attached property called Canvas.Left to inform the parent elemtn (canvas) to position the button 50 units from the left border.

```xml
<Canvas>
  <Button Canvas.Left="50">Hello</Button>
</Canvas>
```

## Border

RelativePanel, StackPanel, and Grid panels define border properties that let you draw a border around the panel without wrapping them in an additional Border element.

```xml
<Grid 
    BorderBrush="Blue" 
    BorderThickness="12" 
    CornerRadius="12" 
    Padding="12">
    <TextBlock Text="Hello World!"/>
</Grid>
```
## RelativePanel

```xml
<RelativePanel BorderBrush="Gray" BorderThickness="1">
    <Rectangle x:Name="RedRect" Fill="Red" Height="44" Width="44"/>
    <Rectangle x:Name="BlueRect" Fill="Blue"
               Height="44" Width="88"
               RelativePanel.RightOf="RedRect" />

    <Rectangle x:Name="GreenRect" Fill="Green" 
               Height="44"
               RelativePanel.Below="RedRect" 
               RelativePanel.AlignLeftWith="RedRect" 
               RelativePanel.AlignRightWith="BlueRect"/>
    <Rectangle Fill="Orange"
               RelativePanel.Below="GreenRect" 
               RelativePanel.AlignLeftWith="BlueRect" 
               RelativePanel.AlignRightWithPanel="True"
               RelativePanel.AlignBottomWithPanel="True"/>
</RelativePanel>
```

## StackPanel


You can use the Orientation property to specify the direction of the child elements. The default orientation is Vertical.

The following XAML shows how to create a vertical StackPanel of items.

```xml
<StackPanel>
    <Rectangle Fill="Red" Height="44"/>
    <Rectangle Fill="Blue" Height="44"/>
    <Rectangle Fill="Green" Height="44"/>
    <Rectangle Fill="Orange" Height="44"/>
</StackPanel>
```
## Grid

```xml
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition/>
        <RowDefinition Height="44"/>
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition/>
    </Grid.ColumnDefinitions>
    <Rectangle Fill="Red" Width="44"/>
    <Rectangle Fill="Blue" Grid.Row="1"/>
    <Rectangle Fill="Green" Grid.Column="1"/>
    <Rectangle Fill="Orange" Grid.Row="1" Grid.Column="1"/>
</Grid>
```


Another example

```xml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition/>
        <ColumnDefinition Width="44"/>
        <ColumnDefinition Width="2*"/>
    </Grid.ColumnDefinitions>
    <TextBlock Text="Column 1 sizes to its conent." FontSize="24"/>
</Grid>
```

| Column |	Sizing	  |Description
|--------|------------|-----------
|Column_1|	Auto	  |The column will size to fit its content.
|Column_2|	*	      |After the Auto columns are calculated, the column gets part of the remaining width. Column_2 will be one-half as wide as Column_4.
|Column_3|	44	      |The column will be 44 pixels wide.
|Column_4|	2*	      |After the Auto columns are calculated, the column gets part of the remaining width. Column_4 will be twice as wide as Column_2.

The default column width is "*", so you don't need to explicitly set this value for the second column.

## VariableSizedWrapGrid

VariableSizedWrapGrid is a Grid-style layout panel where rows or columns automatically wrap to a new row or column when the MaximumRowsOrColumns value is reached.


```xml
<VariableSizedWrapGrid MaximumRowsOrColumns="3" ItemHeight="44" ItemWidth="44">
    <Rectangle Fill="Red"/>
    <Rectangle Fill="Blue" 
               VariableSizedWrapGrid.RowSpan="2"/>
    <Rectangle Fill="Green" 
               VariableSizedWrapGrid.ColumnSpan="2"/>
    <Rectangle Fill="Orange" 
               VariableSizedWrapGrid.RowSpan="2" 
               VariableSizedWrapGrid.ColumnSpan="2"/>
</VariableSizedWrapGrid>
```
In this example, the maximum number of rows in each column is 3. The first column contains only 2 items (the red and blue rectangles) because the blue rectangle spans 2 rows. The green rectangle then wraps to the top of the next column.

## Canvas
The Canvas panel positions its child elements using fixed coordinate points and does not support fluid layouts.

Objects in a Canvas can overlap, where one object is drawn on top of another object. By default, the Canvas renders child objects in the order in which they’re declared, so the last child is rendered on top (each element has a default z-index of 0). 

The Canvas does not do any sizing of its children. Each element must specify its size.

Use the Canvas panel with discretion.

## Panels for ItemsControl

There are several special-purpose panels that can be used only as an ItemsPanel to display items in an ItemsControl. 

These are ItemsStackPanel, ItemsWrapGrid, VirtualizingStackPanel, and WrapGrid. You can't use these panels for general UI layout.



# Review Controls


A control is a UI element that displays content or enables interaction.

We provide 45+ controls for you to use, ranging from simple buttons to powerful data controls like the grid view. These controls are a part of the Fluent Design System and can help you create a bold, scalable UI that looks great on all devices and screen sizes.

There are 3 key steps to adding controls to your app: 
1. Add a control to your app UI, 
1. set properties on the control, and 
1. add code to the control's event handlers so that it does something.

Example WinUI3 Gallery from Windows Store

https://apps.microsoft.com/store/detail/winui-3-gallery/9P3JFPWWDZRC?hl=en-us&gl=us


Review Template Studio Wizard for creating WinUI3 with a wizard. Visual Studi Plugin

https://marketplace.visualstudio.com/items?itemName=TemplateStudio.TemplateStudioForWinUICs


To get started, install the extension, then select the corresponding Template Studio project template when creating a new project in Visual Studio. 

Name your project, then click Create to launch the Template Studio wizard.

Great for getting a project up and running and setting up the app as a file menu or panel app and for creating a list of blank dummy pages.

Relaunch Template Studio to modify the project by 
  - right-clicking on the project in `View -> Solution Explorer` 
  - then selecting `Add -> New Item (Template Studio)`.


