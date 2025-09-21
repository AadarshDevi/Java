# ScatterChart

### Basic Info:
If an fxml is being used, Step 1, 2 can be ignored.

### Step 1: Create Axes
```java
// Create X-Axis
NumberAxis xAxis = new NumberAxis();

// Name Axis
xAxis2.setLabel("X-Axis");

// Create Y-Axis
NumberAxis yAxis = new NumberAxis();

// Name Axis
yAxis2.setLabel("Y-Axis");
```

### Step 2: Create Graph
```java
// Create ScatterChart by passing in xAxis and yAxis
ScatterChart<Number, Number> scatterChart1 = new ScatterChart<Number, Number>(xAxis, yAxis);

// Name the Chart
scatterChart1.setTitle("ScatterChart");
```

### Step 3: Create Data Group
```java
// Create Data Group
XYChart.Series<Double, Double> xyChartSeries = new XYChart.Series<>();

// Name Data Group
xyChart.setName("Group 1");
```

### Step 4: Create Test Data
```java
XYChart.Data<Double, Double> xyChartData1 = new XYChart.Data<>(1.1, 3.7);
XYChart.Data<Double, Double> xyChartData2 = new XYChart.Data<>(1.2, 4.1);
XYChart.Data<Double, Double> xyChartData3 = new XYChart.Data<>(1.3, 4,3);
```

### Step 5: Add Data to Group
```java
xyChart.getData().addAll(xyChartData1, xyChartData2, xyChartData3);
```
