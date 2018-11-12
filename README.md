## three.swift
The ame of the project is to create an easy to use, 3D and 2D drawing and Metal Renderers.

- First of all, I will develop this as some extensions.
    - Camera
    - Primitive Polygon
    - ...
## Development
- Swift 4.2
- Xcode 10.0
- Metal 2

## Usage( Future )

```
import UIKit
import MetalKit

class myRenderVC: UIViewController {
    var renderer: TSRenderer!

    override func viewDidLoad() {
        super.viewDidLoad()
        guard let device = MTLCreateSystemDefaultDevice() else {
            print("Metal is not supported on this device")
            return
        }
        let metalKitView = MTKView(frame: self.view.frame, device: device)
        metalKitView.depthStencilPixelFormat = .depth32Float
        metalKitView.framebufferOnly = true
        
        let box = BoxGeometry(size: 0.5)
        box.rotateX(angle: 0.2)
        renderer.addGeometry(geometry: box)
        
        metalKitView.delegate = renderer
        metalKitView.preferredFramesPerSecond = 60
        
        view = metalKitView
        
        self.renderer.start()
    }
} 
```

## License
MIT
