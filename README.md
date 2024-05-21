# VNTANA Viewer - Jewelry Configurator

Main viewer documentation covering viewer's attributes, properties, and generial interface
can be found [here](https://github.com/VNTANA-3D/viewer-demo). This document specifies
additional functionality necessary for Shah configurators. The functionality is effectively
the same, the only difference being that additional functionality is exposed through functions,
and not viewer methods.

## Demo

In order to run the example provided with this packages, it suffices to run `npm run test`. No prior
installation is needed.

## Functions 

`getSceneGraph(viewer: VntanaViewer): SceneNode`

Returns the root node of viewer's scene graph. Each node has the following entries:
- `type`: description of node's type
- `visible`: indicates whether the node is visible
- `material`: object with properties `name` and `type` (optional)
- `children`: list of node's children (optional)

`printGraph(node: SceneNode): void`

Prints the scene graph rooted at `node` in browser's dev console.

`configureModel(viewer: VntanaViewer, config?: ModelConfig)`

Updates materials and/or visibility of `viewer`'s scene nodes.
The `config` object defines how mesh nodes' visibility and material should be changed.

    {
        "node-name": {
            visible?: boolean,
            material?: string,
        }
        ...
    }

Each mesh in the scene graph with the given name will be updated in the specified way.
If mesh with a given name doesn't exist, the config is ignored. Otherwise, its visiblity will
be set to `visible` and its material to material from Jewelry Library that matches the `material`
name. If any of the properties is omitted, it will stay unchanged.
