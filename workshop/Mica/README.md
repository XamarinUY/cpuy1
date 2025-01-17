# MainPage.xaml 

Agregamos los assets: https://github.com/XamarinUY/cpuy1/blob/master/workshop/Vic/Stickers.zip

invision: https://invis.io/5WR19BMAT7G#/352480367_WelcomeSplash

## ROUND1: Creamos el template del personaje
Creamos un template para cada personaje:
```xaml
<StackLayout BackgroundColor="Black">
    <Frame HasShadow="false" CornerRadius="15" Margin="20" BackgroundColor="Gray" VerticalOptions="FillAndExpand">
        <StackLayout>
            <Label Text="Mario Bros!" TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
            <Image Source="mario_color.png"/>
            <Label Text="Descripción del personaje..." TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
        </StackLayout>
    </Frame>
    <Button Text="CAPTURAR" BackgroundColor="Yellow" TextColor="Black" FontAttributes="Bold" Margin="20,0,20,20"/>
</StackLayout>
``` 

Agregamos los colores que están en el invision:
```xaml
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
            <Label Text="Mario Bros!" TextColor="White" FontSize="Large" FontAttributes="Bold" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
            <Image Source="mario_color.png"/>
            <Label Text="Descripción del personaje..." TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
        </StackLayout>
    </Frame>
    <Button Text="CAPTURAR" BackgroundColor="{StaticResource GoldColor}" TextColor="Black" FontAttributes="Bold" Margin="20,0,20,20"/>
</StackLayout>
```

## ROUND 2: Agregamos el CardsView Plugin 
https://github.com/AndreiMisiukevich/CardView

Como agregar el plugin? en la carpeta Packages de cada proyecto click derecho --> add packages --> buscar "CardsView"

<img src="https://github.com/XamarinUY/cpuy1/blob/master/workshop/Mica/Screen%20Shot%202019-03-15%20at%2012.45.20.png" width="300">

<img src="https://github.com/XamarinUY/cpuy1/blob/master/workshop/Mica/Screen%20Shot%202019-03-14%20at%2022.38.11.png" width="600">

Agregamos la referencia al plugin en el ContentPage: `xmlns: cards="clr-namespace:PanCardView;assembly=PanCardView" `

```xaml
<StackLayout BackgroundColor="{StaticResource BackgroundColor}" Padding="0,30,0,0" VerticalOptions="FillAndExpand">
    <cards:CoverFlowView PositionShiftValue="60" IsCyclical="true" VerticalOptions="FillAndExpand">
        <cards:CoverFlowView.ItemTemplate>
            <DataTemplate>
                <ContentView Padding="40,36,40,15">
                   //Template
                </ContentView>
            </DataTemplate>
        </cards:CoverFlowView.ItemTemplate>
        <!--ItemsSource-->
        <cards:CoverFlowView.ItemsSource>
            <x:Array Type="{x:Type View}">
                <ContentView/>
                <ContentView/>
                <ContentView/>
            </x:Array>
        </cards:CoverFlowView.ItemsSource>
    </cards:CoverFlowView>

    <Button Text="CAPTURAR" BackgroundColor="{StaticResource GoldColor}" TextColor="Black" FontAttributes="Bold" Margin="20,0,20,40"/>
</StackLayout>
```
    
    
