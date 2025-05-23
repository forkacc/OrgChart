![OrgChart](http://dabeng.github.io/OrgChart/img/heading.png)

# [简体文档](https://github.com/dabeng/OrgChart/blob/master/README.zh-cn.md), [繁體文档](https://github.com/dabeng/OrgChart/blob/master/README.zh-tw.md)

# [ES6 Version](http://github.com/dabeng/OrgChart.js)
# [Web Components Version](http://github.com/dabeng/OrgChart-Webcomponents)
# [Vue.js Version](https://github.com/dabeng/vue-orgchart)
# [Angular Version](https://github.com/dabeng/ng-orgchart)
# [React Version](https://github.com/dabeng/react-orgchart)

## Foreword
First of all, thanks a lot for [wesnolte](https://github.com/wesnolte)'s great work:blush: -- [jOrgChart](https://github.com/wesnolte/jOrgChart). The thought that using nested tables to build out the tree-like organization chart is amazing. This idea is more simple and direct than its counterparts based on svg
Unfortunately, it's long time not to see the update of jOrgChart. on the other hand, I got some interesting ideas to add, so I choose to create a new repo. 
- Since version 3.0, we use nested ul to construct tree-like chart instead of nested table.
- Since version 4.0, users build up the ajax datasoure by themselves.

## Features
- Supports both local data and remote data (JSON).
- Smooth expand/collapse effects based on CSS3 transitions.
- Align the chart in 4 orientations.
- Allows user to change orgchart structure by drag/drop nodes.
- Allows user to edit orgchart dynamically and save the final hierarchy as a JSON object.
- Supports exporting chart as a picture or pdf document.
- Supports pan and zoom.
- Allows user to customize the internal structure for every node.
- Users can adopt multiple solutions to build up a huge organization chart(please refer hybrid layout sections).
- touch-enabled plugin for mobile device.

## CDN
Users could find the related CDN support for OrgChart's CSS and JavaScript.

[![cdnjs](https://img.shields.io/cdnjs/v/orgchart)](https://cdnjs.com/libraries/orgchart) https://cdnjs.com/libraries/orgchart

## Installation
Of course, you can directly use the standalone build by including dist/js/jquery.orgchart.js and dist/css/jquery.orgchart.css in your webapps.
### Install with Bower
```
# From version 1.0.2 on, users can install orgchart and add it to bower.json dependencies
$ bower install orgchart
```

### Install with npm
```
# From version 1.0.4 on, users can install orgchart with npm
$ npm install orgchart
```
require('orgchart') will load orgchart plugin onto the jQuery object. The orgchart module itself does not export anything.

FYI, [How to use jQuery Orchart in React](https://stackblitz.com/edit/vitejs-vite-hqv4nbdt)

## [Demos on github pages](https://dabeng.github.io/OrgChart/)
## [Demos based on nested ul](https://codepen.io/collection/xKmPeK)
## [Demos based on nested table](https://codepen.io/collection/AWxGVb/) (obsolete)

### online demos
- [using ul datasource](https://dabeng.github.io/OrgChart/ul-datasource.html)(this feature comes from [Tobyee's good idea :blush:](https://github.com/dabeng/OrgChart/issues/1))

- [using local datasource](https://dabeng.github.io/OrgChart/local-datasource.html)

- [I wanna pan&zoom the orgchart](https://dabeng.github.io/OrgChart/pan-zoom.html)

- I wanna align orgchart with different orientation**(this feature comes from [the good idea of fvlima and badulesia :blush:](https://github.com/dabeng/OrgChart/issues/5))

  Top to Bottom -- default direction, as you can see all other examples on this page.

  [Bottom to Top](https://dabeng.github.io/OrgChart/bottom2top.html)

  [Left to Right](https://dabeng.github.io/OrgChart/left2right.html)

  [Right to Left](https://dabeng.github.io/OrgChart/right2left.html)

- [I wanna show/hide left/right sibling nodes respectively by clicking left/right arrow](https://dabeng.github.io/OrgChart/toggle-sibs-resp.html)

- [I wanna load datasource through ajax](https://dabeng.github.io/OrgChart/ajax-datasource.html)

- [I wanna load data on-demand](https://dabeng.github.io/OrgChart/ondemand-loading-data.html)

![ondemand-loading-data](http://dabeng.github.io/OrgChart/img/ondemand-loading-data.gif)

**Note:** users use should set the relationship property of datasource by themselves. All of these staff are used to generate the correct expanding/collapsing arrows for nodes.

- [I wanna customize the structure of node](https://dabeng.github.io/OrgChart/option-createNode.html)

- [I wanna export the organization chart as a picture](https://dabeng.github.io/OrgChart/export-chart.html)

Here, we need the help from [html2canvas](https://github.com/niklasvh/html2canvas).

**Note:**

(1) if you wanna export something in IE or Edge, please introduce [es6-promise.auto.js](https://github.com/stefanpenner/es6-promise) firstly.

(2) if your OS is windows, please check your display scaling settings. For the perfact exported picture, you'd better adjust "Change the size of text, apps, and other items" to 100%.(thanks for [sayamkrai](https://github.com/sayamkrai)'s [exploration](https://github.com/dabeng/OrgChart/issues/152))

(3) Besides, if you wanna export a pdf format or your orgchart includes picture, you have to introduce [jspdf](https://github.com/MrRio/jsPDF) and set "exportFileextension" option to "pdf".

- [I wanna export the orgchart with nodes containing pictures](https://dabeng.github.io/OrgChart/export-chart-with-pictures.html)

You need to set crossorigin to anonymous for your img tags.

![export-chart-with-pictures](http://dabeng.github.io/OrgChart/img/export-chart-with-pictures.png)

- [I wanna itegrate organization chart with geographic information](https://dabeng.github.io/OrgChart/integrate-map.html)

Here, we fall back on [OpenLayers](https://github.com/openlayers/ol3). It's the most aewsome open-source js library for Web GIS you sholdn't miss.

- [I wanna edit orgchart](https://dabeng.github.io/OrgChart/edit-chart.html)

With the help of exposed core methods(addParent(), addSiblings(), addChildren(), removeNodes()) of orgchart plugin, we can finish this task easily.

- [I wanna drag & drop the nodes of orgchart](https://dabeng.github.io/OrgChart/drag-drop.html)

Users are allowed to drag & drop the nodes of orgchart when option "draggable" is assigned to true(**Note**: this feature doesn't work on IE due to its poor support for HTML5 drag & drop API).

Furthermore, users can make use of option dropCriteria to inject their custom limitations on drag & drop. As shown below, we don't want an manager employee to be under a engineer under no circumstance.

- [I want a method that can describe the hierarchy of orgchart](https://dabeng.github.io/OrgChart/get-hierarchy.html)

That's where getHierarchy() comes in.

- [I want a color-coded chart](https://dabeng.github.io/OrgChart/color-coded.html)

It's a so easy task, we just need to append id or className property to node data.

- [I want a hybrid(horizontal + vertical) chart](https://dabeng.github.io/OrgChart/vertical-level.html)

This feature is inspired by the issues([Aligning Children Vertical](https://github.com/dabeng/OrgChart/issues/46), [Hybrid(horizontal + vertical) OrgChart](https://github.com/dabeng/OrgChart/issues/61)). Thank [mfahadi](https://github.com/mfahadi) and [Destructrix](https://github.com/Destructrix) for their constructive suggestions:blush: Special thanks to [tedliang](https://github.com/tedliang) for his wonderful hybrid mode solution.

From now on, users never have to worry about how to align a huge of nodes in one screen of browser. The option "verticalLevel" allows users to align child nodes vertically from the given level.

**Note**: currently, this option is incompatible with many other options or methods, like direction, drag&drop, addChildren(), removeNodes(), getHierarchy() and so on. These conflicts will be solved one by one in the later versions.

- [I want to collapse some nodes by default](https://dabeng.github.io/OrgChart/default-collapsed.html)

No problem. You just need to adjust a little detail of datasource with the help of option "collapse" and className "slide-up".

- [I want to refresh orgchart base on new options or datasource](https://dabeng.github.io/OrgChart/reload-data.html)

It's not a big deal. You just turn to the method init().

- [I want to use complex template to customize the internal structure of every node](https://dabeng.github.io/OrgChart/custom-template.html)

No problem. With the help of ES6 Template literals, we can customize the any complex node structure rather than the common title and content sections.

- [I want to position node in specific level. How can i do that ?](https://dabeng.github.io/OrgChart/level-offset.html)

![level-offset](http://dabeng.github.io/OrgChart/img/level-offset.png)

You need the solution based on new datasource structure with **levelOffset data prop** + callback createNode() + CSS custom properties(variables)

- [I want a orgchart with nodes of different widths](https://dabeng.github.io/OrgChart/nodes-of-different-widths.html)

![nodes-of-different-widths](http://dabeng.github.io/OrgChart/img/nodes-of-different-widths.png)

- [I want to drag&drop in the hybrid chart](https://dabeng.github.io/OrgChart/drag-drop-hybrid-chart.html)

- [ I only want specific children of a certain branch of the chart to be displayed as vertical. Is it possible to set VerticalLevel by data?](https://dabeng.github.io/OrgChart/data-prop-hybrid.html)

![data-prop-hybrid](http://dabeng.github.io/OrgChart/img/data-prop-hybrid.png)

**hybrid data property** is designed for your use case. Once node data includes a "hybrid" prop with truthy value, its descendant nodes will be arranged vertically.

- [I want to replace built-in icons with Font Awesome icons](https://dabeng.github.io/OrgChart/custom-icons.html)

- [ I want to alternate layout if children is too many](https://dabeng.github.io/OrgChart/data-prop-compact.html)

![data-prop-compact](http://dabeng.github.io/OrgChart/img/data-prop-compact.png)

**compact data property** is designed for your use case. Once node data includes a "compact" prop with truthy value, itself and its descendant nodes will be arranged with compact mode.

- [ I want to visualize genealogy/pedigree/family tree information](https://dabeng.github.io/OrgChart/family-tree.html)

![family-tree](http://dabeng.github.io/OrgChart/img/family-tree.png)

We use the following two-dimensional array datasource to build up the Family Tree. Here, prop "gender" is optional.
```
var datascource = [
  [
    { 'id': '8', 'name': 'Lao Ye', 'title': 'Grandfather' },
    { 
      'id': '1', 'name': 'Lao Lao', 'title': 'Grandmother',  'outsider': true,
      'children': [
        [
          { 'id': '2', 'name': 'Bo miao', 'title': 'Aunt' }
        ],
        [
          { 'id': '3', 'name': 'Su Miao', 'title': 'Mother',
            'children': [
              [
              
                { 'id': '12', 'name': 'Pang Pang', 'title': 'Wife', 'outsider': true,
                  'children': [
                    [{ 'id': '7', 'name': 'Dan Dan', 'title': 'Daughter' }],
                    [{ 'id': '6', 'name': 'Er Dan', 'title': 'Daughter' }],
                  ]
                },
                { 'id': '5', 'name': 'Hei Hei', 'title': 'Me' },
              ]
            ]
          },
          { 'id': '9', 'name': 'Tie Hua', 'title': 'Father', 'outsider': true }
        ],
        [
          { 'id': '10', 'name': 'Hong miao', 'title': 'Aunt' }
        ]
      ]
    }
  ]
];
```

- [I want to add property tags to family tree](https://dabeng.github.io/OrgChart/familytree-custom-properties.html)

![familytree-custom-properties](http://dabeng.github.io/OrgChart/img/familytree-custom-properties.png)

### how to start up demos locally

- you have to install node.js v6+ because our unit tests are based on jsdom v11
- you have to install modern browsers because many behaviors of orgchart plugin are based on HTML5 and CSS3
- run ```npm install``` to install necessary dependencies
- run ```npm test``` to run all tests including unit tests, integration tests and e2e tests
- run ```npm run build``` to generate production js&css files of plugin
- run ```npm start``` to start up local web server to host all the demos

## Usage

### Instantiation Statement
```js
var oc = $('#chartContainerId').orgchart(options);
```

### Structure of Datasource
```js
{
  'id': 'rootNode', // It's a optional property which will be used as id attribute of node
  // and data-parent attribute, which contains the id of the parent node
  'collapsed': true, // By default, the children nodes of current node is hidden.
  'className': 'top-level', // It's a optional property
  // which will be used as className attribute of node.
  'nodeTitle': 'name', // This property is used to retrieve “title” value in datasource
  'nodeContent': 'title',// This property is used to retrieve "content" value in datasource
  'relationship': relationshipValue, // Note: when you activate ondemand loading nodes feature,
  // you should use json datsource (local or remote) and set this property.
  // This property implies that whether this node has parent, siblings, children.
  // relationshipValue is a string composed of three "0/1" identifier.
  // First character stands for wether current node has parent node;
  // Scond character stands for wether current node has siblings nodes;
  // Third character stands for wether current node has children node.
  'children': [ // The property stands for nested nodes.
    { 'name': 'Bo Miao', 'title': 'department manager', 'relationship': '110' },
    { 'name': 'Su Miao', 'title': 'department manager', 'relationship': '111',
      'children': [
        { 'name': 'Tie Hua', 'title': 'senior engineer', 'relationship': '110' },
        { 'name': 'Hei Hei', 'title': 'senior engineer', 'relationship': '110' }
      ]
    },
    { 'name': 'Yu Jie', 'title': 'department manager', 'relationship': '110' }
  ],
  'otherPro': anyValue // feel free to append any useful properties
};
```

### Data Props
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>hybrid</td>
      <td>truthy value</td>
      <td>nodes will be arranged vertically if this property is set to true</td>
    </tr>
    <tr>
      <td>compact</td>
      <td>truthy value</td>
      <td>node will be rendered with compact mode if this property is set to true</td>
    </tr>
  </tbody>
</table>

### Options
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Required</th>
      <th>Default</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>data</td>
      <td>json or jquery object</td>
      <td>yes</td>
      <td></td>
      <td>datasource usded to build out structure of orgchart. It could be a json object or a jquery object(ul element)</td>
    </tr>
    <tr>
      <td>pan</td>
      <td>boolean</td>
      <td>no</td>
      <td>false</td>
      <td>Users could pan the orgchart by mouse drag&drop if they enable this option.</td>
    </tr>
    <tr>
      <td>zoom</td>
      <td>boolean</td>
      <td>no</td>
      <td>false</td>
      <td>Users could zoomin/zoomout the orgchart by mouse wheel if they enable this option.</td>
    </tr>
    <tr>
      <td>zoominLimit</td>
      <td>number</td>
      <td>no</td>
      <td>7</td>
      <td>Users are allowed to set a zoom-in limit.</td>
    </tr>
    <tr>
      <td>zoomoutLimit</td>
      <td>number</td>
      <td>no</td>
      <td>0.5</td>
      <td>Users are allowed to set a zoom-out limit.</td>
    </tr>
    <tr>
      <td>direction</td>
      <td>string</td>
      <td>no</td>
      <td>"t2b"</td>
      <td>The available values are t2b(implies "top to bottom", it's default value), b2t(implies "bottom to top"), l2r(implies "left to right"), r2l(implies "right to left").</td>
    </tr>
    <tr>
      <td>verticalLevel</td>
      <td>integer(>=2)</td>
      <td>no</td>
      <td></td>
      <td>Users can make use of this option to align the nodes vertically from the specified level.</td>
    </tr>
    <tr>
      <td>toggleSiblingsResp</td>
      <td>boolean</td>
      <td>no</td>
      <td>false</td>
      <td>Once enable this option, users can show/hide left/right sibling nodes respectively by clicking left/right arrow.</td>
    </tr>
    <tr>
      <td>visibleLevel</td>
      <td>positive integer</td>
      <td>no</td>
      <td>999</td>
      <td>It indicates the level that at the very beginning orgchart is expanded to.</td>
    </tr>
    <tr>
      <td>nodeTitle</td>
      <td>string</td>
      <td>no</td>
      <td>"name"</td>
      <td>It sets one property of datasource as text content of title section of orgchart node. In fact, users can create a simple orghcart with only nodeTitle option.</td>
    </tr>
    <tr>
      <td>parentNodeSymbol</td>
      <td>string</td>
      <td>no</td>
      <td>"oci-menu"</td>
      <td>Using your own icon to imply that the node has child nodes.</td>
    </tr>
    <tr>
      <td>nodeContent</td>
      <td>string</td>
      <td>no</td>
      <td></td>
      <td>It sets one property of datasource as text content of content section of orgchart node.</td>
    </tr>
    <tr>
      <td>nodeId</td>
      <td>string</td>
      <td>no</td>
      <td>"id"</td>
      <td>It sets one property of datasource as unique identifier of every orgchart node.</td>
    </tr>
    <tr>
      <td>nodeTemplate</td>
      <td>function</td>
      <td>no</td>
      <td></td>
      <td>It's a template generation function used to customize any complex internal structure of node. It receives only one parameter: "data" stands for json datasoure which will be used to render one node.</td>
    </tr>
    <tr>
      <td>createNode</td>
      <td>function</td>
      <td>no</td>
      <td></td>
      <td>It's a callback function used to customize every orgchart node. It receives two parameters: "$node" stands for jquery object of single node div; "data" stands for datasource of single node.</td>
    </tr>
    <tr>
      <td>exportButton</td>
      <td>boolean</td>
      <td>no</td>
      <td>false</td>
      <td>It enable the export button for orgchart.</td>
    </tr>
    <tr>
      <td>exportButtonName</td>
      <td>string</td>
      <td>no</td>
      <td>"Export"</td>
      <td>It's export button name.</td>
    </tr>
    <tr>
      <td>exportFilename</td>
      <td>string</td>
      <td>no</td>
      <td>"Orgchart"</td>
      <td>It's filename when you export current orgchart as a picture.</td>
    </tr>
    <tr>
      <td>exportFileextension</td>
      <td>string</td>
      <td>no</td>
      <td>"png"</td>
      <td>Available values are png and pdf.</td>
    </tr>
    <tr>
      <td>chartClass</td>
      <td>string</td>
      <td>no</td>
      <td>""</td>
      <td>when you wanna instantiate multiple orgcharts on one page, you should add diffent classname to them in order to distinguish them.</td>
    </tr>
    <tr>
      <td>draggable</td>
      <td>boolean</td>
      <td>no</td>
      <td>false</td>
      <td>Users can drag & drop the nodes of orgchart if they enable this option. **Note**: this feature doesn't work on IE due to its poor support for HTML5 drag & drop API.</td>
    </tr>
    <tr>
      <td>dropCriteria</td>
      <td>function</td>
      <td>no</td>
      <td></td>
      <td>Users can construct their own criteria to limit the relationships between dragged node and drop zone. Furtherly, this function accept three arguments(draggedNode, dragZone, dropZone) and just only return boolen values.</td>
    </tr>
    <tr>
      <td>initCompleted</td>
      <td>function</td>
      <td>no</td>
      <td></td>
      <td>It can often be useful to know when your table has fully been initialised, data loaded and rendered. It receives one parament: "$chart" stands for jquery object of initialised chart.</td>
    </tr>
    <tr>
      <td>icons</td>
      <td>json</td>
      <td>no</td>
      <td></td>
      <td>Users can use this option to plug Font Awesome icons back in.
        <pre>
          <code>
'icons': {
  'theme': 'fa-solid fa-sm',
  'parentNode': 'fa-user-tie',
  'expandToUp': 'fa-angles-up',
  'collapseToDown': 'fa-angles-down',
  'collapseToLeft': 'fa-angles-left',
  'expandToRight': 'fa-angles-right',
  'collapsed': 'fa-circle-plus',
  'expanded': 'fa-circle-minus'
}
          </code>
        </pre>
      </td>
    </tr>
    <tr>
      <td>compact</td>
      <td>function</td>
      <td>no</td>
      <td></td>
      <td>This callback is used to determine current node is wether rendered with compact mode. The node's data is passed in as a parameter. <b>Note:</b>The option "compact" has a higher priority than data prop "compact".</td>
    </tr>
  </tbody>
</table>

### Methods
I'm sure that you can grasp the key points of the methods below after you try out demo -- [edit orgchart](http://dabeng.github.io/OrgChart/edit-orgchart/).

#### var oc = $container.orgchart(options)
Embeds an organization chart in designated container. Accepts an options object and you can go through the "options" section to find which options are required. Variable oc is the instance of class OrgChart.

#### init(newOptions)
It's the useful way when users want to re-initialize or refresh orgchart based on new options or reload new data.

#### addAncestors(data, parentId)
Adds the ancestors for current orgchart.
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Required</th>
      <th>Default</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>data</td>
      <td>json</td>
      <td>yes</td>
      <td></td>
      <td>datasource for building ancestors</td>
    </tr>
    <tr>
      <td>parentId</td>
      <td>string</td>
      <td>yes</td>
      <td></td>
      <td>append current orgchart to the parent node with parentId</td>
    </tr>
  </tbody>
</table>

#### addDescendants(data, $parent)
Adds the descendants for specified parent node.
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Required</th>
      <th>Default</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>data</td>
      <td>array</td>
      <td>yes</td>
      <td></td>
      <td>datasource for building descendants</td>
    </tr>
    <tr>
      <td>$parent</td>
      <td>jquery object</td>
      <td>yes</td>
      <td></td>
      <td>append descendants to the $parent node</td>
    </tr>
  </tbody>
</table>

#### addParent(data)
Adds parent node(actullay it's always root node) for current orgchart.
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Required</th>
      <th>Default</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>data</td>
      <td>json object</td>
      <td>yes</td>
      <td></td>
      <td>datasource for building root node</td>
    </tr>
  </tbody>
</table>

#### addSiblings($node, data)
Adds sibling nodes for designated node.
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Required</th>
      <th>Default</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$node</td>
      <td>jquery object</td>
      <td>yes</td>
      <td></td>
      <td>we'll add sibling nodes based on this node</td>
    </tr>
    <tr>
      <td>data</td>
      <td>array</td>
      <td>yes</td>
      <td></td>
      <td>datasource for building sibling nodes</td>
    </tr>
  </tbody>
</table>

#### addChildren($node, data)
Adds child nodes for designed node.
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Required</th>
      <th>Default</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$node</td>
      <td>jquery object</td>
      <td>yes</td>
      <td></td>
      <td>we'll add child nodes based on this node</td>
    </tr>
    <tr>
      <td>data</td>
      <td>array</td>
      <td>yes</td>
      <td></td>
      <td>datasource for building child nodes</td>
    </tr>
  </tbody>
</table>

#### removeNodes($node）
Removes the designated node and its descedant nodes.
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Required</th>
      <th>Default</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$node</td>
      <td>jquery object</td>
      <td>yes</td>
      <td></td>
      <td>node to be removed</td>
    </tr>
  </tbody>
</table>

#### getHierarchy()
This method is designed to get the hierarchy relationships of orgchart for further processing. For example, after editing the orgchart, you could send the returned value of this method to server-side and save the new state of orghcart.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>includeNodeData</td>
    <td>Boolean</td>
    <td>No</td>
    <td>false</td>
    <td>This optional parameter determines whether include the nodeData items in the generated JSON object in addition to the id and children</td>
  </tr>
</table>

#### hideParent($node)
This method allows you to hide programatically the parent node of any specific node(.node element), if it has.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to hide its parent node. Of course, its sibling nodes will be hidden at the same time</td>
  </tr>
</table>

#### showParent($node)
This method allows you to show programatically the parent node of any specific node(.node element), if it has.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to show its parent node</td>
  </tr>
</table>

#### hideChildren($node)
This method allows you to hide programatically the children of any specific node(.node element), if it has.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to hide its children nodes</td>
  </tr>
</table>

#### showChildren($node)
This method allows you to show programatically the children of any specific node(.node element), if it has.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to show its children nodes</td>
  </tr>
</table>

#### hideSiblings($node, direction)
This method allows you to hide programatically the siblings of any specific node(.node element), if it has.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to hide its siblings nodes</td>
  </tr>
  <tr>
    <td>direction</td>
    <td>string</td>
    <td>No</td>
    <td></td>
    <td>Possible values:"left","rigth". Specifies if hide the siblings at left or rigth. If not defined hide both of them.</td>
  </tr>
</table>

#### showSiblings($node, direction)
This method allows you to show programatically the siblings of any specific node(.node element), if it has.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to show its siblings nodes</td>
  </tr>
  <tr>
    <td>direction</td>
    <td>string</td>
    <td>No</td>
    <td></td>
    <td>Possible values:"left","rigth". Specifies if show the siblings at left or rigth. If not defined show both of them.</td>
  </tr>
</table>

#### getNodeState($node, relation)
This method returns you the display state of related node of the specified node.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to know its related nodes' display state.</td>
  </tr>
  <tr>
    <td>relation</td>
    <td>String</td>
    <td>Yes</td>
    <td></td>
    <td>Possible values: "parent", "children" and "siblings". Specifies the desired relation to return.</td>
  </tr>
</table>

The returning object will have the following structure:
```js
{
  "exist": true|false, // Indicates if has parent|children|siblings
  "visible":true|false, // Indicates if the relationship nodes are visible
}
```

#### getRelatedNodes($node, relation)
This method returns you the nodes related to the specified node.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to know its related nodes</td>
  </tr>
  <tr>
    <td>relation</td>
    <td>String</td>
    <td>Yes</td>
    <td></td>
    <td>Possible values: "parent", "children" and "siblings". Specifies the desired relation to return.</td>
  </tr>
</table>

#### getParent($node)
This method returns you the parent node of the specified node.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to know its parent node</td>
  </tr>
</table>

#### getSiblings($node)
This method returns you the sibling nodes of the specified node.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to know its sibling nodes</td>
  </tr>
</table>

#### getChildren($node)
This method returns you the child nodes of the specified node.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$node</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's the desired JQuery Object to know its child nodes</td>
  </tr>
</table>

#### setChartScale($chart, newScale)
This method helps you set the specified chart with new scale.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>$chart</td>
    <td>JQuery Object</td>
    <td>Yes</td>
    <td></td>
    <td>It's a chart in your chart-container</td>
  </tr>
  <tr>
    <td>newScale</td>
    <td>Float</td>
    <td>Yes</td>
    <td></td>
    <td>Positive float value which is used to zoom in/out the chart</td>
  </tr>
</table>

#### export(exportFilename, exportFileextension)
This method allow you to export current orgchart as png or pdf file.
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>exportFilename</td>
    <td>String</td>
    <td>No</td>
    <td>'OrgChart'</td>
    <td>It's the name of exported file</td>
  </tr>
  <tr>
    <td>exportFileextension</td>
    <td>String</td>
    <td>No</td>
    <td>'png'</td>
    <td>It's the extension name of exported file</td>
  </tr>
</table>

### Events
<table>
  <thead>
    <tr>
    <th>Event Type</th>
    <th>Additional Parameters</th>
    <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>nodedrop.orgchart</td>
      <td>draggedNode, dragZone, dropZone</td>
      <td>The event's handler is where you can place your customized function after node drop over. For more details, please refer to <a target="_blank" href="http://dabeng.github.io/OrgChart/drag-drop/">example drag & drop</a>.</td>
    </tr>
    <tr>
      <td>init.orgchart</td>
      <td>chart</td>
      <td>Initialisation complete event - fired when Organization Chart has been fully initialised and data loaded.</td>
    </tr>
    <tr>
      <td>show-[relation].orgchart</td>
      <td></td>
      <td>This event is fired when related nodes of a node become visible.</td>
    </tr>
    <tr>
      <td>hide-[relation].orgchart</td>
      <td></td>
      <td>This event if fired when related nodes of a node are collapsed.</td>
    </tr>
  </tbody>
</table>

### Tips
#### How can I deactivate expand/collapse feature of orgchart?
This use case is inspired by the [issue](https://github.com/dabeng/OrgChart/issues/25). Thanks [der-robert](https://github.com/der-robert) and [ActiveScottShaw](https://github.com/ActiveScottShaw) for their constructive discussions:blush:

Users can enable/disable exapand/collapse feature with className "noncollapsable" as shown below.
```js
$('.orgchart').addClass('noncollapsable'); // deactivate

$('.orgchart').removeClass('noncollapsable'); // activate
```

#### Why is the root node gone?
When I have a huge orgchart with enabled "pan" option, if I hide all the children of one of the topmost parents then the chart disappear from screen. It seems that we need to add a reset button to keep the chart visible.
For details, please refer to the [issue](https://github.com/dabeng/OrgChart/issues/85) opened by [manuel-84](https://github.com/manuel-84) :blush:

Users can embed any clear up logics into the click handler of the reset buttton as shown below.
```js
$('.orgchart').css('transform',''); // remove the tansform settings
```

## Browser Compatibility
- Chrome 19+
- Firefox 4+
- Safari 6+
- Opera 15+
- IE 10+
