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
                    ImageSource = "sonic_color.png"
                },
                new Character()
                {
                    Name = "Mario",
                    Description = "Mario es...",
                    ImageSource = "mario_color.png"
                },
                new Character()
                {
                    Name = "Donkey kong",
                    Description = "Donkey kong es...",
                    ImageSource = "king_kong_color.png"
                }
            };
        }
    }
```

# MainPage.xaml 
## ROUND5(View): Agregamos los Bindings en la View

```xaml

<!--Binding Context-->
<ContentPage.BindingContext>
    <local:MainPageViewModel/>
</ContentPage.BindingContext>

<StackLayout 
    BackgroundColor="{StaticResource BackgroundColor}" 
    Padding="0,30,0,0" 
    VerticalOptions="FillAndExpand">

    <cards:CoverFlowView ItemsSource="{Binding Characters}"
        PositionShiftValue="60" 
        IsCyclical="true" 
        VerticalOptions="FillAndExpand">
        <cards:CoverFlowView.ItemTemplate>
            <DataTemplate>
                <ContentView Padding="40,36,40,15">
                    <Frame HasShadow="false" CornerRadius="15" Padding="20" BackgroundColor="{StaticResource CardBackgroundColor}" VerticalOptions="FillAndExpand">
                        <StackLayout>
                            <Label Text="{Binding Name}" FontSize="Large" FontAttributes="Bold" TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
                            <Image Source="{Binding ImageSource}" />
                            <Label Text="{Binding Description}" TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
                        </StackLayout>
                    </Frame>
                </ContentView>
            </DataTemplate>
        </cards:CoverFlowView.ItemTemplate>
    </cards:CoverFlowView>

    <Button Text="CAPTURAR" BackgroundColor="{StaticResource GoldColor}" TextColor="Black" FontAttributes="Bold" Margin="20,0,20,40"/>
</StackLayout>
```
