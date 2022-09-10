## CODE SNIPPETS

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

