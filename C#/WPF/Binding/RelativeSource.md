# Binding - RelativeSource相对来源绑定

## Mode选择模式
* Self - 当前元素选择器
* FindAncestor - 相对父级选择器
* - AncestorLevel - 相对父级的级别,默认1即上一级
* - AncestorType - 选择的元素类型 例: {x:Type Grid}[必填]
* TemplatedParent - 应该是用于Templte模板获取上级数据用的
* PreviousData - 用于列表数据,显示上一个数据
> PreviousData
```
<collection:ArrayList x:Key="arr">
    <sys:String>文字11</sys:String>
    <sys:String>文字22</sys:String>
    <sys:String>文字33</sys:String>
</collection:ArrayList>
<ListBox ItemsSource="{StaticResource ResourceKey=arr}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <TextBlock Text="{Binding}"/>
                <TextBlock Text="{Binding RelativeSource={RelativeSource Mode=PreviousData}}" Margin="15 0 0 0"/>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox>
```

