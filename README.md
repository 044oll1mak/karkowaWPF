    ﻿using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Data;
    using System.Windows.Documents;
    using System.Windows.Input;
    using System.Windows.Media;
    using System.Windows.Media.Imaging;
    using System.Windows.Navigation;
    using System.Windows.Shapes;

    namespace Wpf_Formularze_3P_sroda
    {
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            etykieta.FontSize = suwak.Value;
        }
    }
    }   
    <Window x:Class="Wpf_Formularze_3P_sroda.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:Wpf_Formularze_3P_sroda"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <StackPanel>
        <TextBlock 
            FontSize="{Binding ElementName=suwak, Path=Value}"
            Background="DarkViolet"
            Foreground="Wheat"
            TextAlignment="Center"
            Margin="20"
            Padding="10"
            x:Name="tekst"
            >
            Jakiś tekst
        </TextBlock>
        <Slider Minimum="20"
               Maximum="45"
                x:Name="suwak"
                />
        <Label
            x:Name="etykieta"
            Content="inny napis"/>
        <Label>jakis napis</Label>
        <Button Width="200"
                Click="Button_Click"
                >Zmien rozmiar tekstu
        </Button>
    </StackPanel>
    </Window>








  


    ﻿using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Data;
    using System.Windows.Documents;
    using System.Windows.Input;
    using System.Windows.Media;
    using System.Windows.Media.Imaging;
    using System.Windows.Shapes;

    namespace Wpf_Formularze_3P_sroda
    {
    /// <summary>
    /// Logika interakcji dla klasy WindowKalkulator.xaml
    /// </summary>
    public partial class WindowKalkulator : Window
    {
        public WindowKalkulator()
        {
            InitializeComponent();
        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            if(int.TryParse(liczba1.Text, out int a) && int.TryParse(liczba2.Text,out int b) )
            {
                int w = a + b;
                wynik_label.Content ="Wynik dodawania:"+  w;
            }
        }
    }
    }
    ﻿<Window x:Class="Wpf_Formularze_3P_sroda.WindowKalkulator"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:Wpf_Formularze_3P_sroda"
        mc:Ignorable="d"
        Title="WindowKalkulator" Height="450" Width="800">
    <StackPanel>
        <Label Content="Podaj pierwszą liczbę"/>
        <TextBox x:Name="liczba1"/>
        <Label Content="Podaj drugą liczbę"/>
        <TextBox x:Name="liczba2"/>
        <Button Click="Button_Click">Oblicz sumę</Button>
        <Label>Wpisano</Label>
        <Label Content="{Binding ElementName=liczba1,Path=Text}"/>
        <Label Content="{Binding ElementName=liczba2,Path=Text}"/>
        <Label x:Name="wynik_label"/>
    </StackPanel>
    </Window>












    ﻿using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Data;
    using System.Windows.Documents;
    using System.Windows.Input;
    using System.Windows.Media;
    using System.Windows.Media.Imaging;
    using System.Windows.Shapes;

    namespace Wpf_Formularze_3P_sroda
    {
    /// <summary>
    /// Logika interakcji dla klasy WindowKwadrat.xaml
    /// </summary>
    public partial class WindowKwadrat : Window
    {
        public WindowKwadrat()
        {
            InitializeComponent();
        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            String wpisanyBok = bok_txt.Text;
            kwadrat.Fill = (SolidColorBrush)new BrushConverter().ConvertFromString(kolorki.Text);
            if(przezrocz_chbox.IsChecked == true) {
                kwadrat.Opacity = 0.5;
            }
            else
            {
                kwadrat.Opacity = 1;
            }
            if(widoczny.IsChecked == true)
            {
                kwadrat.Visibility = Visibility.Visible;
            }
            if(ukryty.IsChecked == true)
            {
                kwadrat.Visibility = Visibility.Hidden;
            }
            double bok;
            MessageBox.Show("Wpisano: " + wpisanyBok, "Wartość wpisana",
                MessageBoxButton.OK, MessageBoxImage.Information);
            if(double.TryParse(wpisanyBok, out  bok) ) 
            {
                double pole = bok * bok;
                wynik_pole_txt.Text = pole.ToString();
                double obwod = 4 * bok;
                wynik_obwod_txt.Text = obwod.ToString();

                kwadrat.Width = bok;
                kwadrat.Height = bok;


            }
            else
            {
                MessageBox.Show("Musisz wpisać liczbę rzeczywistą");
                wynik_obwod_txt.Text = "";
                wynik_pole_txt.Text = string.Empty;
            }
        }

        private void bok_txt_TextChanged(object sender, TextChangedEventArgs e)
        {
            if(double.TryParse(bok_txt.Text,out double boczek))
            {
                kwadrat.Width = boczek * 2;
                kwadrat.Height = boczek * 2;
                
            }
        }
    }
    }
    <Window x:Class="Wpf_Formularze_3P_sroda.WindowKwadrat"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:Wpf_Formularze_3P_sroda"
        mc:Ignorable="d"
        Title="Obliczenia dla kwadratu"
        Height="450" Width="800">
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*"/>
            <ColumnDefinition Width="*"/>
            <ColumnDefinition Width="auto"/>
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
        </Grid.RowDefinitions>
        <TextBlock 
            Margin="10"
            FontSize="20">
            Bok kwadratu
        </TextBlock>
        <TextBlock 
            Margin="10"
            FontSize="20"
            Grid.Row="1"
            >
            Pole kwadratu
        </TextBlock>
        <TextBlock 
            Margin="10"
            FontSize="20"
            Grid.Row="2"
            >
            Obwód kwadratu
        </TextBlock>
        <TextBox
            Grid.Column="1"
            Margin="10"
            x:Name="bok_txt"
            
            TextChanged="bok_txt_TextChanged"
            >
        </TextBox>
        <TextBlock x:Name="wynik_pole_txt"
                   FontSize="20"
                   Grid.Column="1"
                   Grid.Row="1"/>
        <TextBlock x:Name="wynik_obwod_txt"
                   FontSize="20"
                   Grid.Column="1"
                   Grid.Row="2"/>
        <Button Content="Oblicz"  
                Grid.Row="6"
                Margin="20"
                Grid.ColumnSpan="2"
                Click="Button_Click"/>
        <Rectangle
            Width="{Binding ElementName=bok_txt,Path=Text}"
            Height="{Binding ElementName=bok_txt,Path=Text}"
            Fill="{Binding ElementName=kolorki, Path=Text}"
            Grid.Row="3"
            />
        <Rectangle
            Width="20"
            Height="20"
            Fill="Orange"
            Margin="2"
            Grid.Row="4"
            x:Name="kwadrat"
            />
        <ComboBox x:Name="kolorki"
                  Grid.Column="1"
                  Grid.Row="4"
                  Margin="10"
                  SelectedIndex="0">
            <ComboBoxItem>Red</ComboBoxItem>
            <ComboBoxItem>Green</ComboBoxItem>
            <ComboBoxItem>Blue</ComboBoxItem>
            <ComboBoxItem>Fuchsia</ComboBoxItem>
        </ComboBox>
        <CheckBox
            Grid.Row="5"
            IsChecked="True"
            Margin="20"
            x:Name="przezrocz_chbox"
            >
            Przeźroczysty?
        </CheckBox>
        <StackPanel
            Grid.Column="1"
        Grid.Row="5">
            <RadioButton GroupName="widocznosc"
                         x:Name="widoczny">
                Widoczny
            </RadioButton>
            <RadioButton GroupName="widocznosc"
                         x:Name="ukryty"
                         IsChecked="True">
                Ukryty
            </RadioButton>
        </StackPanel>

    </Grid>
    </Window>
