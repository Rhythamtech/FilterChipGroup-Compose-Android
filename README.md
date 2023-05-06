# FilterChipGroup-Compose-Android
How to Create FilterChipGroup  step-by-step:

1. Define the `FilterChipGroup` function with parameters:

   - `items`: A list of strings representing the filter chip labels.
   - `defaultSelectedItemIndex`: Index of the initially selected item.
   - `selectedItemIcon`: Representing the icon for the selected item (Optional).
   - `itemIcon`:Representing the icon for unselected items (Optional).
   - `onSelectedChanged`: A callback function to be called when the selected item changes, passing the selected index.

   Example:
   ```kotlin
   @Composable
   fun FilterChipGroup(
       items: List<String>,
       defaultSelectedItemIndex: Int = 0,
       selectedItemIcon: ImageVector = Icons.Filled.Done,
       itemIcon: ImageVector = Icons.Filled.Build,
       onSelectedChanged: (Int) -> Unit = {}
   )
   ```

2. Create a `selectedItemIndex` mutableState to store the currently selected item index. Initialize it with the `defaultSelectedItemIndex`.

   ```kotlin
   var selectedItemIndex by remember { mutableStateOf(defaultSelectedItemIndex) }
   ```

3. Create a `LazyRow` to display the filter chips horizontally and allow scrolling and create `FilterChips` for all items in the `items` list.

   ```kotlin
   LazyRow(userScrollEnabled = true) {
   
   items(items.size) { index: Int ->
   }
   }
   ```

4. Inside the loop, create a `FilterChip`:
   ```kotlin
   FilterChip(
       modifier = Modifier.padding(end = 6.dp),
       selected = items[selectedItemIndex] == items[index],
       onClick = {
           selectedItemIndex = index
           onSelectedChanged(index)
       },
       label = { Text(items[index]) },
       leadingIcon = if (items[selectedItemIndex] == items[index]) {
           {
               Icon(
                   imageVector = selectedItemIcon,
                   contentDescription = "Localized Description",
                   modifier = Modifier.size(FilterChipDefaults.IconSize)
               )
           }
       } else {
           {
               Icon(
                   imageVector = itemIcon,
                   contentDescription = "Localized description",
                   modifier = Modifier.size(FilterChipDefaults.IconSize)
               )
           }
       }
   )
   ```

I hope you understand the step-by-step procedure for creating the FilterChipGroup Composable. You can use this function to create a scrollable list of filter chips that can be used as RadioButton with customizable icons and a callback that returns selectedItemIndex for when the selected item changes.

## Screenshots

![Custom-Filter-Chip-Group-using-Jetpack-Compose-in-Android-1](https://i.ibb.co/kcg15Rh/Custom-Filter-Chip-Group-using-Jetpack-Compose-in-Android-1.png)
