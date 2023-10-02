
<h1>HW1</h1>
<table>
  <tr>
    <td>
    <img src="https://raw.githubusercontent.com/AmilyC/Yzu-swiftui/main/Hw1.png">  
    </td>
    <td>
      
 ```swift
    import SwiftUI
    struct ContentView: View {
        var body: some View {
            Image("Sf")
                .resizable()
                .aspectRatio(contentMode: .fit)
                .clipShape(RoundedRectangle(cornerRadius: /*@START_MENU_TOKEN@*/25.0/*@END_MENU_TOKEN@*/, style: /*@START_MENU_TOKEN@*/.continuous/*@END_MENU_TOKEN@*/), style: /*@START_MENU_TOKEN@*/FillStyle()/*@END_MENU_TOKEN@*/)
                .overlay(
                    Text("姓名：陳姿蓉\n學號：1103344")
                        .fontWeight(.medium)
                        .lineSpacing(10)
                        .font(.system(size: 15))
                        .foregroundColor(.white)
                        .frame(width: 150, height: 75, alignment:.center)
                        .background(Color.orange)
                        .cornerRadius(30, antialiased: /*@START_MENU_TOKEN@*/true/*@END_MENU_TOKEN@*/)
                        .opacity(/*@START_MENU_TOKEN@*/0.8/*@END_MENU_TOKEN@*/)
                    ,
                    alignment: .bottomLeading
                )
            Image(systemName: "tag")
                .foregroundColor(.orange)
                .font(.system(size:25))
                .frame(width: 350,height: 15,alignment:.leading )
                .padding(5)
            Text("咖哩是不拌派\n火鍋不能加芋頭\n滷肉飯用湯匙吃\n寫程式的時候一定要戴耳機")
                .font(.body)
                .fontWeight(.light)
                .padding(10)
                .lineSpacing(/*@START_MENU_TOKEN@*/10.0/*@END_MENU_TOKEN@*/)
            
        }
    }

      
 ```

  <img src="https://raw.githubusercontent.com/AmilyC/Yzu-swiftui/main/Hw1.png">
     </td>
  </tr>
</table>
