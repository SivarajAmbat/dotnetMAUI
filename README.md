## CODE SNIPPETS FOR DEMO SESSION

## Creating UI in C#
```
namespace MauiAppCS
{
    public partial class MainPage : ContentPage
    {
         public MainPage()
        {
            InitializeComponent();

            var sv = new ScrollView();

            sv.Background = new SolidColorBrush(Colors.DarkGrey);
            sv.Margin = new Thickness(10, 10, 10, 10);
            var sl = new VerticalStackLayout();
            sv.Content = sl;

            this.Content = sv;

        }  
    }
}
```
## Equivalent in XAML	
```
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MauiAppCS.MainPage" Background="SlateGrey">
    <ScrollView Background="DarkSlateGrey" Margin="10,20">
        <VerticalStackLayout>
        </VerticalStackLayout>
    </ScrollView>
</ContentPage>
```

## Pages

### ContentPage	
```
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MauiAppCS.NewPage1"
             Title="NewPage1">
    <VerticalStackLayout>
        <Label 
            Text="Welcome to .NET MAUI!"
            VerticalOptions="Center" 
            HorizontalOptions="Center" />
    </VerticalStackLayout>
</ContentPage>
```

### NavigationPage

```
// Define first page as a NavigationPage in App.xaml.cs	
    public partial class App : Application
    {
        public App()
        {
            InitializeComponent();

            MainPage = new NavigationPage(new NewPage1());
        }
    }

// To navigate to another page: 
	
	private void Button_Clicked(object sender, EventArgs e)
	{
		Navigation.PushAsync(new NewPage2());
	}


// To navigate back:	
	private void Button_Clicked(object sender, EventArgs e)
	{
		Navigation.PopAsync();
	}
```
### FlyoutPage
```
// In code-behind file:	

public partial class FlyoutPage1 : FlyoutPage
{
	public FlyoutPage1()
	{
		InitializeComponent();
	}
}

// Markup:	

<?xml version="1.0" encoding="utf-8" ?>
<FlyoutPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
            xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
            x:Class="MauiApp2.FlyoutPage1"
            Title="FlyoutPage1"
            FlyoutLayoutBehavior="Popover">
    <FlyoutPage.Flyout>
        <ContentPage Title="My App">
            <VerticalStackLayout>
                <Label Text="Home" />
            </VerticalStackLayout>
        </ContentPage>
    </FlyoutPage.Flyout>
    <FlyoutPage.Detail>
        <ContentPage>
            <VerticalStackLayout>
                <Label Text="Hello World" />
            </VerticalStackLayout>
        </ContentPage>
    </FlyoutPage.Detail>
</FlyoutPage>
```
### TabbedPage
```
// TabbedPage markup:

<?xml version="1.0" encoding="utf-8" ?>
<TabbedPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
            xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
            x:Class="MauiApp2.TabbedPage1"
            Title="TabbedPage1"
            BarBackgroundColor="Navy"
            BarTextColor="White"
            SelectedTabColor="White"
            UnselectedTabColor="LightSteelBlue">
    <ContentPage Title="Page 1"
                 IconImageSource="dotnet_bot.svg">
        <Label Text="Demo Page 1" />
    </ContentPage>
    <ContentPage Title="Page 2"
                 IconImageSource="dotnet_bot.svg">
        <Label Text="Demo Page 2" />
    </ContentPage>
    <ContentPage Title="Page 3"
                 IconImageSource="dotnet_bot.svg">
        <Label Text="Demo Page 3" />
    </ContentPage>
</TabbedPage>

// Ensure to make changes in C#:	

public partial class TabbedPage1 : TabbedPage
{
	public TabbedPage1()
	{
		InitializeComponent();
	}
}
```
## Layouts

### AbsoluteLayout
```
    <AbsoluteLayout>
        <Button Text="Click"
                AbsoluteLayout.LayoutBounds="0,300,0.5,0.5"
                AbsoluteLayout.LayoutFlags="SizeProportional" />
    </AbsoluteLayout>
```
### StackLayout
```
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MauiApp2.StackLayout1"
             Title="StackLayout1">
    <StackLayout Orientation="Vertical"
                 Spacing="10">
        <Label Text="Label"
               VerticalOptions="Center"
               HorizontalOptions="Start"
               BackgroundColor="LightBlue" />
        <Label Text="Label"
               VerticalOptions="Center"
               HorizontalOptions="Center"
               BackgroundColor="LightPink" />
        <Label Text="Label"
               VerticalOptions="Center"
               HorizontalOptions="End"
               BackgroundColor="LightGreen" />
        <Label Text="Label"
               VerticalOptions="Center"
               HorizontalOptions="Fill"
               BackgroundColor="LightSlateGrey" />
    </StackLayout>
</ContentPage>
```
### Grid
```
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MauiApp2.StackLayout1"
             Title="StackLayout1">
    <Grid RowDefinitions="*,*"
          ColumnDefinitions="*,*"
          ColumnSpacing="5"
          RowSpacing="5">
        <Button Text="0,0"
                Grid.Row="0"
                Grid.Column="0" />
        <Button Text="0,1"
                Grid.Row="0"
                Grid.Column="1" />
        <Button Text="1,0"
                Grid.Row="1"
                Grid.Column="0" />
        <Button Text="1,1"
                Grid.Row="1"
                Grid.Column="1" />
    </Grid>
</ContentPage>
```





### Controls
// TO-DO

## Styles
// TO-DO

## Data Binding - Binding to UI controls
### Binding with BindingContext

```
       <VerticalStackLayout>

            <Label x:Name="lblTitle"
                   BindingContext="{x:Reference Name=slr}"
                   FontSize="{Binding Path=Value}"
                   Text="Hello World" />
                        
            <Slider x:Name="slr"
                    Maximum="100"
                    Minimum="10"
                    Value="14" />

        </VerticalStackLayout>


// Equivalent C# code:

            lblTitle.BindingContext = slr;
            lblTitle.SetBinding(Label.FontSizeProperty, "Value");

```
### Binding without a binding context
```
        <VerticalStackLayout>

            <Label x:Name="lblTitle"
                   Text="Hello World"
                   FontSize="{Binding Source={x:Reference slr},Path=Value}" />

            <Slider x:Name="slr"
                    Maximum="100"
                    Minimum="10"
                    Value="14" />

        </VerticalStackLayout>

// Equivalent C# code:
            lblTitle.SetBinding(Label.FontSizeProperty, new Binding("Value", source: slr));

```
## Data Binding - Binding to Objects
```
// Collection 

namespace CollectionsTrial
{
    public partial class MainPage : ContentPage
    {
        public Contact friend;

        public List<Contact> contacts = new List<Contact>() {
        new Contact { Name = "John Doe", MobileNumber = "9901234567", ImageUrl = "johndoe.png" },
        new Contact { Name = "Peter Parker", MobileNumber = "9902134567", ImageUrl  = "peterparker.png" },
        new Contact { Name = "Tony Stark", MobileNumber = "9903124567", ImageUrl = "tonystark.png" },
        new Contact { Name = "John Doe", MobileNumber = "9901234567", ImageUrl = "johndoe.png" },
        new Contact { Name = "Peter Parker", MobileNumber = "9902134567", ImageUrl  = "peterparker.png" },
        new Contact { Name = "Tony Stark", MobileNumber = "9903124567", ImageUrl = "tonystark.png" },
        new Contact { Name = "John Doe", MobileNumber = "9901234567", ImageUrl = "johndoe.png" },
        new Contact { Name = "Peter Parker", MobileNumber = "9902134567", ImageUrl  = "peterparker.png" },
        new Contact { Name = "Tony Stark", MobileNumber = "9903124567", ImageUrl = "tonystark.png" },
        };

        public MainPage()
        {
            InitializeComponent();
            friend = new Contact { Name = "John Doe", MobileNumber = "9901234567", ImageUrl = "Blue" };
            this.Loaded += MainPage_Loaded;
        }

        private void MainPage_Loaded(object sender, EventArgs e)
        {
            //scrollView.BindingContext = friend;
            contactsView.ItemsSource = contacts;
        }
    }
}

// Model

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace CollectionsTrial
{
    public class Contact
    {
        public string Name { get; set; }
        public string MobileNumber { get; set; }
        public string ImageUrl { get; set; }
    }
}


// View

<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="CollectionsTrial.MainPage"
             Title="My Contacts"
             BackgroundColor="DarkSlateGrey">

    <!--<ScrollView x:Name="scrollView">
        <VerticalStackLayout
            Spacing="25"
            Padding="30,0"
            VerticalOptions="Start">
            <Label Text="Contact Detail" />
        </VerticalStackLayout>
    </ScrollView>-->

    <CollectionView x:Name="contactsView"
                    Background="Navy">
        <CollectionView.ItemTemplate>
            <DataTemplate>
                <Grid RowDefinitions="*,*"
                      ColumnDefinitions="100,*"
                      Background="Black"
                      Margin="5"
                      Padding="10">
                    <Image Source="{Binding ImageUrl}"
                           HeightRequest="70"
                           WidthRequest="70"
                           Grid.Row="0"
                           Grid.Column="0"
                           Grid.RowSpan="2" />
                    <Label Text="{Binding Name}"
                           FontSize="24"
                           TextColor="Orange"
                           FontAttributes="Bold"
                           Grid.Row="0"
                           Grid.Column="1" />
                    <Label Text="{Binding MobileNumber}"
                           FontSize="18"
                           TextColor="White"
                           Grid.Row="1"
                           Grid.Column="1" />
                </Grid>
            </DataTemplate>
        </CollectionView.ItemTemplate>
    </CollectionView>
</ContentPage>
```


```

