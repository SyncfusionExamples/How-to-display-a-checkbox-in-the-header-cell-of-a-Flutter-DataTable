## How to display a checkbox in the header cell of a Flutter DataTable?

In this article, we will show you how to display a checkbox in the header cell of a [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with all the necessary properties. Achieve this by loading the [checkbox](https://api.flutter.dev/flutter/material/Checkbox-class.html) widget as a child within the designated [GridColumn](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn-class.html). Initialize a map collection to track the state of each checkbox. The keys should correspond to the column names, and the values should represent whether the checkbox is checked or not. In the [onChanged](https://api.flutter.dev/flutter/material/Checkbox/onChanged.html) callback of each checkbox, update the state of the corresponding checkbox in the map using setState, and perform your desired action. Then, retrieve the names of the checked columns using the map collection.

```dart
  Map<String, bool> checkedColumns = {
    'id': false,
    'name': false,
    'designation': false,
    'salary': false,
  };

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: Column(
        children: [
          TextButton(
              onPressed: () {
                // To fetch the checked column names.
                List<String> checkedColumnNames = checkedColumns.entries
                    .where((entry) => entry.value)
                    .map((entry) => entry.key)
                    .toList();
              },
              child: const Text('Checked column')),
          Expanded(
            child: SfDataGrid(
              source: employeeDataSource,
              columnWidthMode: ColumnWidthMode.fill,
              columns: <GridColumn>[
                GridColumn(
                    columnName: 'id',
                    label: Container(
                      padding: const EdgeInsets.all(16.0),
                      alignment: Alignment.center,
                      child: Row(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          const Text('ID'),
                          Checkbox(
                            value: checkedColumns['id'],
                            onChanged: (bool? value) {
                              setState(() {
                                checkedColumns['id'] = value!;
                              });
                            },
                          ),
                        ],
                      ),
                    )),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                      padding: const EdgeInsets.all(8.0),
                      alignment: Alignment.center,
                      child: Row(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          const Text('Name'),
                          Checkbox(
                            value: checkedColumns['name'],
                            onChanged: (bool? value) {
                              setState(() {
                                checkedColumns['name'] = value!;
                              });
                            },
                          ),
                        ],
                      ),
                    )),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                      padding: const EdgeInsets.all(8.0),
                      alignment: Alignment.center,
                      child: Row(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          const Text(
                            'Designation',
                            overflow: TextOverflow.ellipsis,
                          ),
                          Checkbox(
                            value: checkedColumns['designation'],
                            onChanged: (bool? value) {
                              setState(() {
                                checkedColumns['designation'] = value!;
                              });
                            },
                          ),
                        ],
                      ),
                    )),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                      padding: const EdgeInsets.all(8.0),
                      alignment: Alignment.center,
                      child: Row(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          const Text('Salary'),
                          Checkbox(
                            value: checkedColumns['salary'],
                            onChanged: (bool? value) {
                              setState(() {
                                checkedColumns['salary'] = value!;
                              });
                            },
                          ),
                        ],
                      ),
                    )),
              ],
            ),
          ),
        ],
      ),
    );
  }
```

You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-display-a-checkbox-in-the-header-cell-of-a-Flutter-DataTable).