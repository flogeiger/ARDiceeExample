# ARDiceeExample
ARDiceeExample integrates Appl to show your latest step and weight data in animated, interactive Swift Charts. 

# Technologies Used
* SwiftUI
* DocC
* Git & GitHub
* ARKit

# Example of App usage
https://github.com/user-attachments/assets/7d2185e4-e9d3-4d93-baab-475d5aa55ebf

# I'm Most Proud Of...
First Project to use ARKit for Augmented Reality Apps.

Here's the code:

```swift
override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
        if let touch = touches.first{
            let touchLocation = touch.location(in: sceneView)
            let hitResults = sceneView.hitTest(touchLocation, types: .existingPlaneUsingExtent)
            
            if let hitResult = hitResults.first{
                let diceScene = SCNScene(named: "art.scnassets/diceCollada.scn")!
                
                if let diceNode = diceScene.rootNode.childNode(withName: "Dice", recursively: true){
                    
                    diceNode.position = SCNVector3(
                        hitResult.worldTransform.columns.3.x,
                        hitResult.worldTransform.columns.3.y + diceNode.boundingSphere.radius,
                        hitResult.worldTransform.columns.3.z)
                    
                    diceArray.append(diceNode)
                    
                    sceneView.scene.rootNode.addChildNode(diceNode)
                    
                    roll(dice: diceNode)
                }
            }
        }
    }
```
<br>
</br>


# Completeness
Although it's a simple portfolio project, I've implemented the following
* First impressions with ARKit
