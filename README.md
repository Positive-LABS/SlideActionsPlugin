SlideActionsPlugin
==================

Plugin for Sencha Touch 2 lists to add buttons showing on item swipe.
Only one item has actions at once. When you tap on item or swipe another one, it closes any open actions container.

Screenshot
==========

My List:

![alt tag](https://raw.githubusercontent.com/Positive-LABS/SlideActionsPlugin/master/ScreenShots/SlideActionsPlugin-ss1.png)

First item actions:

![alt tag](https://raw.githubusercontent.com/Positive-LABS/SlideActionsPlugin/master/ScreenShots/SlideActionsPlugin-ss2.png)

Second item actions:

![alt tag](https://raw.githubusercontent.com/Positive-LABS/SlideActionsPlugin/master/ScreenShots/SlideActionsPlugin-ss3.png)

Installation
============

Copy whole PLabs dir at root of your ST project. Add new PLabs classpath :

For dev:

```
/* app.js */
//<debug>
Ext.Loader.setConfig({
    enabled : true,
    paths   : {
        'Ext': 'touch/src',
        'Ux' : './Ux',
        'PLabs': './PLabs',
        'MyApp': 'app',
    }
});
//</debug>


```

For production:

```
/* .sencha/app/sencha.cfg */

...
app.classpath=${app.dir}/Ux,${app.dir}/PLabs,${app.dir}/app.js,${app.dir}/app
...

/* .sencha/workspace/sencha.cfg */

...
app.classpath=${app.dir}/Ux,${app.dir}/PLabs,${app.dir}/app.js,${app.dir}/app
...

```

Usage
=====

In your list, use the plugin:

```
Ext.define('MyApp.view.test.List', {
    extend: 'Ext.List',
    xtype: 'testList',
    requires: ['PLabs.plugin.SlideActions'],
    config: {
        store: 'Tests',
        plugins: {
            xclass: 'PLabs.plugin.SlideActions',
            buttons: [
                {
                    xtype: 'button',
                    // text: 'Share',
                    html: "<img src='resources/images/share.png'+"' style='width: 30px'>",
                    //iconCls: 'share',
                    ui: 'action',
                    listeners: {
                        tap: function(button){
                            console.log(button.getRecord());
                            console.log('clicked on share button of record '+button.getRecord().getId());
                        },
                        scope: this
                    }
                },
                {
                    xtype: 'button',
                    // text: 'Delete',
                    html: "<img src='resources/images/delete.png'+"' style='width: 30px'>",
                    //iconCls: 'delete',
                    ui: 'decline',
                    listeners: {
                        tap: function(button){
                            console.log(button.getRecord());
                            console.log('clicked on delete button of record '+button.getRecord().getId());
                        },
                        scope: this
                    }
                }
            ]
        },
        ....
```

That's it !

Configuration
=============

There are some config parameters to customize render:

```
buttons: [],            //Your buttons, don't forget to add xtype: 'button'.
minDrag: 100,           //Min number of pixels that the user must slide before the plugin disables list scroll and starts to show buttons. Don't put it to 0 !! If not, your list will never scroll
openPosition: 350,      //Width of panel containing buttons
animation: {duration: 250, easing: {type: 'ease-out'}}, //Slide animation to open buttons container
actionsBackground: "#5b5b5b", //Background color of buttons container
itemBackground: '#ffffff'  //Background color of your list items
```
