# MainPage.xaml 
## ROUND1: Creamos el template del personaje

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
                <Label Text="Mario Bros!" TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
                <Label Text="Descripción del personaje..." TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
            </StackLayout>
        </Frame>
        <Button Text="CAPTURAR" BackgroundColor="{StaticResource GoldColor}" TextColor="Black" FontAttributes="Bold" Margin="20,0,20,20"/>
    </StackLayout>
</ContentPage>
```
## ROUND 2: Agregamos el CardsView Plugin 
https://github.com/AndreiMisiukevich/CardView

Como agregar el plugin? en la carpeta Packages de cada proyecto click derecho --> add packages --> buscar "CardsView"

![image](https://github.com/XamarinUY/cpuy1/blob/master/workshop/Mica/Screen%20Shot%202019-03-15%20at%2012.45.20.png =100x100)


![alt text](https://github.com/XamarinUY/cpuy1/blob/master/workshop/Mica/Screen%20Shot%202019-03-14%20at%2022.38.11.png)

Agregamos la referencia al plugin en el ContentPage: `xmlns: cards="clr-namespace:PanCardView;assembly=PanCardView" `

```xaml
    <StackLayout BackgroundColor="{StaticResource BackgroundColor}" Padding="0,30,0,0" VerticalOptions="FillAndExpand">
        <cards:CoverFlowView PositionShiftValue="60" IsCyclical="true" VerticalOptions="FillAndExpand">
            <cards:CoverFlowView.ItemTemplate>
                <DataTemplate>
                    <ContentView Padding="40,36,40,15">
                        <Frame HasShadow="false" CornerRadius="15" Padding="20" BackgroundColor="{StaticResource CardBackgroundColor}" VerticalOptions="FillAndExpand">
                            <StackLayout>
                                <Label Text="Mario Bros!" TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
                                <Label Text="Descripción del personaje..." TextColor="White" HorizontalOptions="Center" VerticalOptions="CenterAndExpand" />
                            </StackLayout>
                        </Frame>
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
    
    
