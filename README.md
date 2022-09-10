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

