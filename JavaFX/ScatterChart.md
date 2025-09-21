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
XYChart.Series<Double, Double> xyChart = new XYChart.Series<>();

// Name Data Group
xyChart.setName("Group 1");
```

### Step 4: Create Test Data
```java
```
