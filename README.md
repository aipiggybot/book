# book

```swift
var str = "Hello, playground"

extension String {

  subscript (index: Int) -> Character {
    let charIndex = self.index(self.startIndex, offsetBy:index)
    return self[charIndex]
  }

  subscript (range: Range<Int>) -> String {
    let startIndex = self.index(self.startIndex, offsetBy:range.lowerBound)

    if self.count > range.upperBound {
      let endIndex = self.index(startIndex, offsetBy:range.upperBound)
      return String(self[startIndex..<endIndex])
    }
    return String(self[startIndex..<self.endIndex])
  }

  // BE  Begin End
  func findBE(_ str: String) -> (Int,Int)? {
    if let r = self.range(of: str) {
      return (r.lowerBound.encodedOffset, r.upperBound.encodedOffset)
    }
    return nil
  }
  func find(_ str: String) -> Int? {
    if let r = self.range(of: str) {
      return r.lowerBound.encodedOffset
    }
    return nil
  }
}

str[3..<7]  // "lo, pla"

if let (x,y) = "Test box".findBE("box") {
  print("Text box"[x..<y])     // "box"
  print("x = \(x), y = \(y)")  // x = 5, y =8
}

str.find("play")  // 7
```



> This is a block quote



