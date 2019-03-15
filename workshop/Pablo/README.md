# ROUND6: Creamos una pagina de navegacion custom

<img src="https://github.com/XamarinUY/cpuy1/blob/master/workshop/Pablo/Captura%20de%20pantalla%202019-03-15%20a%20la(s)%2015.38.31.png" width="300">

<img src="https://github.com/XamarinUY/cpuy1/blob/master/workshop/Pablo/Captura%20de%20pantalla%202019-03-15%20a%20la(s)%2015.39.04.png" width="600">

## CustomNavigationPage.xaml 

```xaml
<?xml version="1.0" encoding="UTF-8"?>
<NavigationPage xmlns="http://xamarin.com/schemas/2014/forms" xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml" x:Class="RetroGamesGO.CustomNavigationPage">
    
</NavigationPage>

```

## CustomNavigationPage.xaml.cs

```c#
    public partial class CustomNavigationPage : NavigationPage
    {
        public CustomNavigationPage(Page root) : base(root)
        {
            InitializeComponent();
        }
    }
```

# ROUND7: Registramos la navegacion
## App.xaml.cs 

```c#
    ...
    public App()
    {
        InitializeComponent();

        MainPage = new CustomNavigationPage(new MainPage());
    }
    ...
```

Ahora, creamos una nueva pagina a la cual navegar llamada CaptureView (de la misma forma que agregamos la CustomNavigationPage).

# ROUND8: Navegamos al hacer click en Capturar
## MainPageViewModel.cs 

```c#
    ...

    public ICommand CaptureCommand => new Command(Capture);

    private void Capture()
    {
        var navigation = Application.Current.MainPage as CustomNavigationPage;
        if (navigation != null)
        {
            navigation.PushAsync(new CaptureView(), true);
        }
    }

    ...
```

## MainPage.xaml 

```xaml
    ...
    
    <Button Text="CAPTURAR" BackgroundColor="{StaticResource GoldColor}" TextColor="Black" FontAttributes="Bold" Margin="20,0,20,40" Command="{Binding CaptureCommand}" />
    
    ...
```


# ROUND9: Customizamos la barra de navegacion
## CustomNavigationPage.xaml

```xaml

<?xml version="1.0" encoding="UTF-8"?>
<NavigationPage xmlns="http://xamarin.com/schemas/2014/forms" xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml" x:Class="RetroGamesGO.CustomNavigationPage"
                BarBackgroundColor="#121619" BarTextColor="White">
</NavigationPage>

```
