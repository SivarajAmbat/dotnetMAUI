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
