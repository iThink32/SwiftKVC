# SwiftKVC
Swift KVC Without @objc Runtime using Mirror (Reflection)

## What is it ?

If you need KYC in Swift you have to rely on @objc runtime , exposing models to objc etc.To avoid all that you can use mirror to achieve exactly that.Just make your model confirm to the protocol StringAccessible and your done.

## Procedure ?

Make your model conform to the protocol 

```
struct MarketMoverResponseModel:Decodable,StringAccessible {
    let topGainer:[StockResponseModel]?
    let topLoser:[StockResponseModel]?
    let week52High:[StockResponseModel]?
    let week52Low:[StockResponseModel]?
    let valueGainer:[StockResponseModel]?
    let volumeGainer:[StockResponseModel]?
}
```

following which you can call the method in the extension on an object of the struct like 

```
let result:[StockResponseModel] = obj.getValueFor(key:"topGainer")
```

where obj is an object of the struct/class that conforms to the protocol.
