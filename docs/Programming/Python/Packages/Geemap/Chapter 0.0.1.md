
## Use Data: GLC-FCS30D

https://gee-community-catalog.org/projects/glc_fcs/

```Python
import ee
import geemap
geemap.ee_initialize()
FCS30D = ee.ImageCollection("projects/sat-io/open-datasets/GLC-FCS30D/annual")
image = FCS30D.mosaic(); image
map = geemap.Map()

def recodeClasses(image):
    classes = [10, 11, 12, 20, 51, 52, 61, 62, 
               71, 72, 81, 82, 91, 92, 120, 121, 
               122, 130, 140, 150, 152, 153, 181, 
               182, 183, 184, 185, 186, 187, 190, 
               200, 201, 202, 210, 220, 0]
    reclassed = image.remap(classes, ee.List.sequence(1, len(classes)))
    return reclassed

palette = [
  "#ffff64", "#ffff64", "#ffff00", "#aaf0f0", "#4c7300", "#006400", "#a8c800", "#00a000", 
  "#005000", "#003c00", "#286400", "#285000", "#a0b432", "#788200", "#966400", "#964b00", 
  "#966400", "#ffb432", "#ffdcd2", "#ffebaf", "#ffd278", "#ffebaf", "#00a884", "#73ffdf", 
  "#9ebb3b", "#828282", "#f57ab6", "#66cdab", "#444f89", "#c31400", "#fff5d7", "#dcdcdc", 
  "#fff5d7", "#0046c8", "#ffffff", "#ffffff"
]
vis_params = {"min": 1, "max": 36, "palette": palette}

def addLayer(image, name):
    map.addLayer(image, vis_params ,name)

for i in range(1,23):
    year = 1999 + i
    layerName = "GLC FCS " + str(year)
    band = image.select("b" + str(i))
    addLayer(recodeClasses(band), layerName)

map
```

## Download Data: GLC-FCS30D

```shell
conda install -c conda-forge geedim -y
```

```Python
import ee
import geemap

geemap.ee_initialize()
# 直接读取geojson
edge_ee = geemap.geojson_to_ee(r"C:\Users\Qiao\Documents\FireEdge.geojson")
# FeatureCollection转Feature 此时是线
edge = ee.Feature(edge_ee.toList(edge_ee.size()).get(0))
# 将LinearRing转换为坐标，再转换为多边形
edge_face = ee.Geometry.Polygon(edge_ee.geometry().coordinates())
map = geemap.Map()
map.addLayer(edge_face, {}, "edge")
map
# 读取数据集
FCS30D = ee.ImageCollection("projects/sat-io/open-datasets/GLC-FCS30D/annual")
image = FCS30D.mosaic(); image
image_2022 = (
    image.select("b23")
    .clip(edge_face).unmask()
)

# 数据集样式文件
def recodeClasses(image):
    classes = [10, 11, 12, 20, 51, 52, 61, 62, 
               71, 72, 81, 82, 91, 92, 120, 121, 
               122, 130, 140, 150, 152, 153, 181, 
               182, 183, 184, 185, 186, 187, 190, 
               200, 201, 202, 210, 220, 0]
    reclassed = image.remap(classes, ee.List.sequence(1, len(classes)))
    return reclassed
palette = [
  "#ffff64", "#ffff64", "#ffff00", "#aaf0f0", "#4c7300", "#006400", "#a8c800", "#00a000", 
  "#005000", "#003c00", "#286400", "#285000", "#a0b432", "#788200", "#966400", "#964b00", 
  "#966400", "#ffb432", "#ffdcd2", "#ffebaf", "#ffd278", "#ffebaf", "#00a884", "#73ffdf", 
  "#9ebb3b", "#828282", "#f57ab6", "#66cdab", "#444f89", "#c31400", "#fff5d7", "#dcdcdc", 
  "#fff5d7", "#0046c8", "#ffffff", "#ffffff"
]
vis_params = {"min": 1, "max": 36, "palette": palette}

map.addLayer(recodeClasses(image_2022), vis_params ,"image_2022"); map

geemap.download_ee_image(
    image_2022, 
    filename="GLC-FCS30D-2022-ROI.tif", 
    scale=30, 
    region=edge_face,
    crs='EPSG:4326',
    max_tile_dim = 512
)
```