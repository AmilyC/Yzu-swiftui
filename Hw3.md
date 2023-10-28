<h1>HW3</h1>
<table>
  <tr>
    <td>
```swift
      import SwiftUI

struct ContentView: View {
    var body: some View {
        
        VStack{
            TitleView().background(Color(red: 247/255,green: 217/255,blue: 76/255)).cornerRadius(15).opacity(/*@START_MENU_TOKEN@*/0.8/*@END_MENU_TOKEN@*/)
            HStack{
                //PlantView()
                itemView(imageName: "P2")
                ZStack{
                    itemView(imageName: "P1")
                    Text("catus")
                        .font(.custom("Noteworthy", size: 30))
                        .background(Color(red: 247/255,green: 217/255,blue: 76/255))
                        .cornerRadius(15, antialiased: /*@START_MENU_TOKEN@*/true/*@END_MENU_TOKEN@*/)
                        .offset(x: 0, y: 50)
                        .opacity(/*@START_MENU_TOKEN@*/0.8/*@END_MENU_TOKEN@*/)
                        .frame(width: 120, height: 60, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                }
                
                itemView(imageName: "P3")
                
            }
            
            //boxView()
            HStack{
                //itemView
                ZStack{
                    VStack{
                        paperView(imageName: "Postcard2")
                        paperView(imageName: "Postcard3")
                        paperView(imageName: "Postcard4")
                    }
                    Text("postcard")
                        .frame(width:120, height: 60, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                        .font(.custom("Noteworthy", size: 30))
                        .background(Color(red: 247/255,green: 217/255,blue: 76/255))
                        .cornerRadius(15, antialiased: /*@START_MENU_TOKEN@*/true/*@END_MENU_TOKEN@*/)
                        .offset(x: 0, y: 65)
                        .opacity(/*@START_MENU_TOKEN@*/0.8/*@END_MENU_TOKEN@*/)
                }.padding(10)
                
                //paperView(imageName: "Postcard")
                
                paperView(imageName: "Paper1")
                ZStack{
                    //
                    paperView(imageName: "Paper2")
                    Text("paper tape")
                        .frame(width:120, height: 60, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                        .font(.custom("Noteworthy", size: 30))
                        .background(Color(red: 247/255,green: 217/255,blue: 76/255))
                        .cornerRadius(15, antialiased: /*@START_MENU_TOKEN@*/true/*@END_MENU_TOKEN@*/)
                        .offset(x: -50, y: 70)
                        .opacity(/*@START_MENU_TOKEN@*/0.8/*@END_MENU_TOKEN@*/)
                }
                
                //PlantView
            }
            //boxView
            HStack{
                ZStack{
                    itemView(imageName: "Earphone")
                    Text("earphone")
                        .frame(width:120, height: 60, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                        .font(.custom("Noteworthy", size: 30))
                        .background(Color(red: 247/255,green: 217/255,blue: 76/255))
                        .cornerRadius(15, antialiased: /*@START_MENU_TOKEN@*/true/*@END_MENU_TOKEN@*/)
                        .offset(x: 0, y: 70)
                        .opacity(/*@START_MENU_TOKEN@*/0.8/*@END_MENU_TOKEN@*/)
                }
                ZStack{
                    itemView(imageName: "Star")
                    Text("paper star")
                        .frame(width:120, height: 60, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                        .font(.custom("Noteworthy", size: 30))
                        .background(Color(red: 247/255,green: 217/255,blue: 76/255))
                        .cornerRadius(15, antialiased: /*@START_MENU_TOKEN@*/true/*@END_MENU_TOKEN@*/)
                        .offset(x: 0, y: 70)
                        .opacity(/*@START_MENU_TOKEN@*/0.8/*@END_MENU_TOKEN@*/)
                }
                ZStack{
                    itemView(imageName: "Flower")
                    Text("flower")
                        .frame(width:120, height: 60, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                        .font(.custom("Noteworthy", size: 30))
                        .background(Color(red: 247/255,green: 217/255,blue: 76/255))
                        .cornerRadius(15, antialiased: /*@START_MENU_TOKEN@*/true/*@END_MENU_TOKEN@*/)
                        .offset(x: 0, y: 70)
                        .opacity(/*@START_MENU_TOKEN@*/0.8/*@END_MENU_TOKEN@*/)
                }
                
                //itemView()
                //itemView()
            }
        }.background(Image("Bg1"))
    }
}
struct TitleView: View {
    var body: some View {
        Text("Amily's 收藏架")
            .font(.custom("Noteworthy", size: 30))
            .foregroundColor(Color.black)
            
    }
}
struct paperView:View{
    var imageName:String
    var body:some View{
        VStack{
            Image(imageName)
                .resizable()
                .aspectRatio(contentMode: .fit)
                .frame(width: 120,height:160,alignment: .center)
        }.frame(minWidth: /*@START_MENU_TOKEN@*/0/*@END_MENU_TOKEN@*/, idealWidth: 50, maxWidth: /*@START_MENU_TOKEN@*/.infinity/*@END_MENU_TOKEN@*/, minHeight: /*@START_MENU_TOKEN@*/0/*@END_MENU_TOKEN@*/, idealHeight: 50, maxHeight: /*@START_MENU_TOKEN@*/.infinity/*@END_MENU_TOKEN@*/, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/).padding(10)
    }
}
struct itemView:View{
    var imageName:String
    var body:some View{
        VStack{
            Image(imageName)
                .resizable()
                .aspectRatio(contentMode: .fit)
                .frame(width: 100,height:150,alignment: .center)
        }.frame(minWidth: /*@START_MENU_TOKEN@*/0/*@END_MENU_TOKEN@*/, idealWidth: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, maxWidth: /*@START_MENU_TOKEN@*/.infinity/*@END_MENU_TOKEN@*/, minHeight: /*@START_MENU_TOKEN@*/0/*@END_MENU_TOKEN@*/, idealHeight: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, maxHeight: /*@START_MENU_TOKEN@*/.infinity/*@END_MENU_TOKEN@*/, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        
    }
}
extension UIScreen{
    static let screenWidth = UIScreen.main.bounds.size.width
    static let screenHeight = UIScreen.main.bounds.size.height
    static let screenSize = UIScreen.main.bounds.size
}

```
    </td>
  </tr>
</table>
