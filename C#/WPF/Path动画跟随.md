# 设置Path动画跟随
```
<Window x:Class="WpfTest.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfTest"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Window.Resources>
        <!-- 使用Blend的铅笔绘制路线 -->
        <PathGeometry x:Key="PathData" Figures="M0,0 C11.575841,32.265198 13.810697,36.784279 23.333333,40.593333 27.68923,42.335692 29.4801,42.103283 34.166667,39.76 37.475304,38.105682 40.363316,35.730018 43.166667,32.926667 46.274133,29.8192 49.663917,27.761375 53.666667,25.76 55.383952,24.901357 57.004706,24.369543 58.833333,23.76 60.962519,23.050272 62.851057,22.91521 65.166667,23.093333 69.263689,23.408489 69.800455,26.627349 72.333333,30.426667 74.215171,33.249424 76.660785,36.730592 77.333333,40.093333 79.554638,40.981855 79.28136,41.610658 82.333333,40.593333 85.036863,39.692157 87.942903,39.077129 90.666667,38.26 100.21271,35.396186 108.93355,34.570022 119.16667,35.593333 125.15535,36.192202 129.92579,34.796507 132,43.093333 132.98115,47.017952 132.59517,52.617014 134.33333,56.093333 137.13898,53.287687 140.16371,52.66603 143.83333,51.093333 147.15322,49.670527 151.23199,47.792662 155.16667,49.76 158.37534,51.364335 158.07675,54.913495 159.66667,58.093333 162.2059,63.171802 163.53408,69.353712 165.5,74.76 166.37451,77.16491 167.5,79.460124 167.5,82.093333 167.5,83.792831 167.78296,84.510614 166.83333,86.093333 164.96432,89.208349 163.8513,88.76 159.33333,88.76 140.7769,88.76 122.43012,87.331687 104,84.26 91.974511,82.255752 95.956079,83.838825 90.5,72.926667 89.269712,70.46609 88.219711,67.695202 86.5,65.593333 83.834466,62.335458 85.219742,61.593333 79.833333,61.593333 73.245269,61.593333 70.06535,64.351726 63.833333,67.26 60.287198,68.914863 56.87757,70.623084 53.5,72.593333 50.863023,74.13157 48.512496,75.580838 46.333333,77.76 41.046894,83.046439 44,85.779972 44,94.26 43.903812,93.682873 43.707057,93.100622 43.5,92.593333"/>
    </Window.Resources>
    <Grid>
        <Canvas>
            <Path Panel.ZIndex="5" Canvas.Top="65" Canvas.Left="65" Stroke="Red" Data="{StaticResource PathData}" StrokeThickness="1"/>
            <Button RenderTransformOrigin="0.5,0.5" Canvas.Top="50" Canvas.Left="50" Width="30" Height="30" Content="b">
                <!-- 给Button创建一个Matrix -->
                <Button.RenderTransform>
                    <MatrixTransform/>
                </Button.RenderTransform>
                <!-- 创建Button点击事件 -->
                <Button.Triggers>
                    <EventTrigger RoutedEvent="Button.Click">
                        <BeginStoryboard>
                            <Storyboard>
                                <MatrixAnimationUsingPath 
                                    Duration="0:0:10"
                                    <!-- 操作Matrix -->
                                    Storyboard.TargetProperty="RenderTransform.Matrix" 
                                    DoesRotateWithTangent="True"
                                    PathGeometry="{StaticResource PathData}"/>
                            </Storyboard>
                        </BeginStoryboard>
                    </EventTrigger>
                </Button.Triggers>
            </Button>
        </Canvas>
    </Grid>
</Window>

```