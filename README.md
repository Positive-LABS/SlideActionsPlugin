SlideActionsPlugin
==================

Plugin for Sencha Touch 2 lists to add buttons showing on item swipe

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
