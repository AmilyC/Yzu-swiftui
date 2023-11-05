<h1>HW2</h1>
<table>
  <tr>
    
    
```swift
import SwiftUI
var ran:Int=0
var strP:String=""
struct ContentView: View {
   // @State var ran:Int=0
    @State var ranCom:Int=0
    @State var type=["Scissor","Stone","Paper"]
    @State var str:String=""
    @State var strCom:String=""
    var body: some View {
        
        VStack {
            
            
            Text(String("   computer："+strCom))
                .padding(.all,20)
                .frame(width: 400, height: 60, alignment:.leading)
                //.font(.system(size:30,design: .rounded))
                .font(.custom("Noteworthy",size:40))
            Text(String("   player："))
                .padding(.all,20)
                .frame(width: 400, height: 60, alignment: .leading)
                .font(.custom("Noteworthy", size: 40))
          //  HStack{
                FruitView(imageName: "Stone")
                //FruitView(imageName: "Paper")
                //FruitView(imageName: "Scissor")

          //  }
            
            
            
            Button(action: {
               // self.ran=Int.random(in: 0...2)
                self.ranCom=Int.random(in: 0...2)
                strCom=type[self.ranCom]
                if ran==ranCom{
                    str="tie~"
                }else if ran==0{
                    if ranCom==1{
                        str="You lose!"
                    }else{
                        str="You win!"
                    }
                }
                else if ran==1{
                    if ranCom==0{
                         str="You lose!"
                    }else{
                         str="You win!"
                    }
                }
                else{
                    if ranCom==0{
                         str="You lose!"
                    }else{
                         str="You win!"
                    }
                }
               // print(ran)
                }, label: {
                Text("GO")
                    .padding(.all,10)
                    .frame(width: 300, height: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                    .font(.custom("Noteworthy", size: 50))
                    .background(Color.teal)
                    .foregroundColor(Color.white)
                    .border(Color.clear, width: /*@START_MENU_TOKEN@*/1/*@END_MENU_TOKEN@*/)
                    .cornerRadius(30, antialiased: /*@START_MENU_TOKEN@*/true/*@END_MENU_TOKEN@*/)
            })
            Text(String(str))
                .padding(.all,10)
                .frame(width: 500, height: 200, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
                .font(.custom("Noteworthy", size: 50))
            
        }.background(Image("Big").opacity(0.3))
           // .frame(width: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, height: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
        
    }
}

struct FruitView: View{
    var imageName:String
   
    @State var now:Int=0
    @State var C=[Color.clear,Color.clear,Color.clear]
    var body: some View {
    
        HStack{
            
            Button(action:{
                C[1]=Color.yellow
                C[0]=Color.clear
                C[2]=Color.clear
                ran=1
            }, label: {
                Image("Stone")
                    .resizable()
                    .aspectRatio( contentMode: .fit)
                    .frame(width:100,height: 150, alignment: .center)
                    .border(C[1], width: 4)
    
            })
            Button(action:{
                C[2]=Color.yellow
                C[0]=Color.clear
                C[1]=Color.clear
                ran=2
                
            }, label: {
                Image("Paper")
                    .resizable()
                    .aspectRatio( contentMode: .fit)
                    .frame(width:100,height: 150, alignment: .center)
                    .border(C[2], width: 4)
                
            })
            Button(action:{
                ran=0
                C[0]=Color.yellow
                C[1]=Color.clear
                C[2]=Color.clear
            }, label: {
                Image("Scissor")
                    .resizable()
                    .aspectRatio( contentMode: .fit)
                    .frame(width:100,height: 150, alignment: .center)
                    .border(C[0], width: 4)
                
            })
        }
    }
}

```


 <img src="https://raw.githubusercontent.com/AmilyC/Yzu-swiftui/main/Hw2-

https://github.com/AmilyC/Yzu-swiftui/assets/91866786/1334cc25-4644-4dc8-8dd8-7023ecf4fe35

1.jpg">
 <img src="https://raw.githubusercontent.com/AmilyC/Yzu-swiftui/main/HW2-2.jpg">
 <img src = "https://raw.githubusercontent.com/AMilyC/Yzu-swiftui/main/HW2-3.jpg">
    </td>
  </tr>
</table>
