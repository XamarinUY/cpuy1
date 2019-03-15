# Character.cs 
## ROUND3 (Model): Agregamos el modelo para los personajes

```c#
  public class Character
  {
      public string Name { set; get; }
      public string Description { set; get; }
      public string ImageSource { set; get; }
  }
```

# MainPageViewModel.cs 
## ROUND4 (ViewModel): Creamos el MainPageViewModel

```c#
    public class MainPageViewModel : INotifyPropertyChanged
    {
        public event PropertyChangedEventHandler PropertyChanged;

        protected void OnPropertyChanged(string propertyName)
        {
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
        }

        private List<Character> _characters;
        public List<Character> Characters
        {
            get { return _characters; }
            set
            {
                _characters = value;
                OnPropertyChanged("Characters");
            }
        }

        public MainPageViewModel()
        {
            LoadCharacters();
        }

        private void LoadCharacters()
        {
            Characters = new List<Character>()
            {
                new Character()
                {
                    Name = "Sonic",
                    Description = "Sonic es...",
                    ImageSource = ""
                },
                new Character()
                {
                    Name = "Mario",
                    Description = "Mario es...",
                    ImageSource = ""
                },
                new Character()
                {
                    Name = "Donkey kong",
                    Description = "Donkey kong es...",
                    ImageSource = ""
                }
            };
        }
    }
```

# MainPage.xaml 
## ROUND5(View): Agregamos los Bindings en la View

```xaml
<?xml version="1.0" encoding="utf-8"?>
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms" 
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml" 
             xmlns:local="clr-namespace:Test" 
             x:Class="Test.MainPage">
    
    <ContentPage.Resources>
        <ResourceDictionary>
            <Color x:Key="BackgroundColor">#121619</Color>
            <Color x:Key="CardBackgroundColor">#191e23</Color>
            <Color x:Key="GoldColor">#f8b82f</Color>
            <Color x:Key="GrayColor">#999999</Color>
        </ResourceDictionary>
    </ContentPage.Resources>
    
    <StackLayout BackgroundColor="{StaticResource BackgroundColor}">
        <Frame HasShadow="false" CornerRadius="15" Margin="20" BackgroundColor="{StaticResource CardBackgroundColor}" VerticalOptions="FillAndExpand">
            <StackLayout>
                <Label Text="{Binding Name}" TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
                <Image Source="{Binding ImageSource}" />
                <Label Text="{Binding Description}" TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
            </StackLayout>
        </Frame>
        <Button Text="CAPTURAR" BackgroundColor="{StaticResource GoldColor}" TextColor="Black" FontAttributes="Bold" Margin="20,0,20,20"/>
    </StackLayout>
</ContentPage>
```
