
<h1>HW4</h1>
<table>
  <tr>
    
    
```swift
import SwiftUI

struct ContentView: View {
    @AppStorage("IsDeepScheme") var isDeepScheme: Bool = false
    var body: some View {
        
        VStack {
            
            TabView {
                Group {
                    
                    WelcomeView()
                        .tabItem {
                            Image(systemName: "house")
                            Text("Home")
                        }
                    CourseListView()
                        .tabItem {
                            Image(systemName: "books.vertical")
                            Text("Your Library")
                        }
                    SearchView()
                   // Text("hi")
                        .tabItem {
                            Image(systemName: "magnifyingglass")
                            Text("Search")
                        }
                    TrendView()
                        .tabItem {
                            Image(systemName: "flame.fill")
                            Text("Trends")
                        }
                    SettingView()
                        .tabItem {
                            Image(systemName: "gearshape.fill")
                            Text("Setting")
                        }
                }
                .toolbarBackground(tabColor()[1], for: .tabBar)
                .toolbarBackground(.visible, for: .tabBar)
            }
           .tint(tabColor()[0])
        }
        .padding(.top, 20)
        .background(tabColor()[1])
    }
    
}

struct BrowseView:View{
    //    var IsDeepScheme:Bool
    var image:String
    var TypeName:String
    var body:some View{
        VStack{
            Image(image)
                .resizable()
                .aspectRatio(contentMode: .fit)
            VStack(alignment: .leading, content: {
                Text(TypeName)
                    .font(.headline)
                    .foregroundStyle(.secondary)
                    .foregroundColor(tabColor()[0])
            })
            .frame(minWidth: 0,idealWidth: 100, maxWidth: .infinity, alignment: .leading)
            .padding(.leading, 15)
            .padding(.bottom, 10)
            
        }
        .background(tabColor()[1])
        //.clipShape(.rect(cornerRadius: 20))
        .overlay(
            RoundedRectangle(cornerRadius: 0)
                .stroke(Color.white, lineWidth: 2)
        )
        .padding(.all, 10)
    }
}
struct Course: Identifiable{
    var id = UUID()
    var image:String
    var courseNameUS:String
    var courseNameTW:String
    var description:String
    
}
var courses=[Course(image: "Topmix1", courseNameUS: "Artist", courseNameTW: "Ed Sheeran", description:"76.4M monthly listeners" ),
             Course(image: "Topmix2", courseNameUS: "Artist", courseNameTW: "imase", description:"4.1M monthly listeners"),
             Course(image: "Topmix3", courseNameUS: "Artist", courseNameTW: "10cm", description:"1M monthly listeners"),
             Course(image: "Topmix4", courseNameUS: "Artist", courseNameTW: "Keira Knightley", description:"323.3k monthly listeners"),
             Course(image: "Topmix5", courseNameUS: "Artist", courseNameTW: "Zooey Wonder", description: "43.5k monthly listeners"),
]
struct CourseListView: View {
    @State var showDetailView = false
    @State var selectCourse:Course?//value may be empty
    var body: some View {
        //
        VStack{
            TitleView(text: "Your Library")
            NavigationView{
                
                List(courses){
                    coursetItem in
                    
                    BasicImageRow(thisCourse: coursetItem)
                        .listRowBackground(tabColor()[1])
                    //.listRowSeparatorTint(Color.gray)
                        .onTapGesture {
                            //what happen will click the list
                            self.showDetailView=true
                            self.selectCourse=coursetItem
                            
                        }
                    //BasicImageRow(thisRestaurant: restaurantItem)
                }
                .background(tabColor()[1])
                .scrollContentBackground(.hidden)
                .sheet(item: self.$selectCourse,content:{
                    thisCourse in
                    CourseDetailView(thisCourse: thisCourse)
                        .background(tabColor()[1])
                })
                
            }
            // .background(tabColor()[1])
        }
        .background(tabColor()[1])
        
        
        
    }
}
struct BasicImageRow: View{
    var thisCourse:Course
    var body: some View{
        HStack{
            
            Image(thisCourse.image)
                .resizable()
                .frame(width: 40 ,height: 40)
                .cornerRadius(5)
            VStack{
                Text(thisCourse.courseNameTW)
                    .font(.headline)
                    .foregroundStyle(.primary)
                    .foregroundStyle(tabColor()[0])
                    .frame(width: 120, alignment: .leading)
                Text(thisCourse.courseNameUS)
                    .font(.headline)
                    .foregroundStyle(.secondary)
                    .foregroundStyle(tabColor()[0])
                    .frame(width: 120, alignment: .leading)
            }
            
            
        }
        
        
        
    }
}
struct CourseDetailView: View{
    @Environment(\.presentationMode) var presentationMode
    var thisCourse:Course
    var body: some View{
        ScrollView{
            VStack{
                Image(thisCourse.image)
                    .resizable()
                    .aspectRatio(contentMode: .fit)
                    .clipped()
                //.frame(width: 40, height: 40)
                //.cornerRadius(5)
                Text(thisCourse.courseNameTW)
                    .font(.system(.title, design: .rounded, weight: .black))
                    .foregroundColor(tabColor()[0])
                Spacer()
                Text(thisCourse.description)
                    .font(.system(.subheadline, design: .rounded))
                    .fontWeight(.light)
                    .foregroundColor(tabColor()[0])
                Spacer()
                
            }
        }.overlay(
            HStack{
                Spacer()
                VStack{
                    Button(action:{
                        self.presentationMode.wrappedValue.dismiss()
                    },label: {
                        Image(systemName: "chevron.down.circle.fill")
                            .font(.largeTitle)
                            .foregroundColor(.white)
                        
                    })
                    .padding(.trailing, 20)//increase right distance
                    .padding(.top, 20)
                    Spacer()
                }
            }
        )
    }
}

// search
struct SongType: Identifiable{
    var id = UUID()
    var image:String
    var SongType:String
    
}
var songTs=[
    SongType(image: "1", SongType: "Music"),
    SongType(image: "1", SongType: "Live Events"),
    SongType(image: "1", SongType: "New Releases"),
    SongType(image: "1", SongType: "Mandopop"),
    SongType(image: "1", SongType: "K-pop")
    
]
struct SearchView:View{
    //Binding var text: String
    @AppStorage("SearchText") var SearchText:String = ""
    //State var text:String
    @State var isEditing=false
    var body:some View{
        VStack{
            TitleView(text: "Search")
            HStack{
                TextField("Search...",text: $SearchText)
                    .padding(7)
                    .padding(.horizontal,25)
                    .background(Color(.systemGray6))
                    .cornerRadius(8)
                    .overlay{
                        HStack{
                            Image(systemName: "magnifyingglass")
                                .foregroundColor(.secondary)
                                .frame(minWidth:0 ,maxWidth: .infinity,alignment: .leading)
                                .padding(.leading,8)
                            if isEditing{
                                Button(action: {
                                    self.SearchText=""
                                }, label: {
                                    Image(systemName: "multiply.circle.fill")
                                        .foregroundColor(.secondary)
                                        .padding(.trailing, 8)
                                })
                            }
                        }
                    }
                    .padding(.horizontal, 10)
                    .onTapGesture{
                        self.isEditing=true
                    }
                if isEditing{
                    Button(action: {
                        self.isEditing = false
                        self.SearchText = ""
                    }, label: {
                        Text("Cancel")
                            .foregroundColor(tabColor()[0])
                    })
                    .padding(.trailing,10)
                    .transition(.move(edge: .trailing))
                    //.animation(.default)
                }
            }
            .frame(minWidth: 0, idealWidth: 100,maxWidth: .infinity, alignment: .leading)
            ScrollView()
            {
                HStack{
                    TypeView(TypeSet: songTs, TitleName: "")
                    TypeView(TypeSet: songTs, TitleName: "")
                }
                
            }
            
            
        }
        .background(tabColor()[1])
        .padding(.leading,0)
        
        
        
        
    }
}
struct TypeView: View{
    var TypeSet: [SongType]
    var TitleName:String
    // var isDark:Bool
    var body: some View{
        VStack{
            ForEach(TypeSet){
                thisType in
                BrowseView(image: thisType.image, TypeName: thisType.SongType)
            }
            
        }
        
    }
}

//Setting
struct SettingView: View {
    let displayFontType = [".default",".rounded",".monospaced",".serif"]
    @State var displayFontSelected = 0
    @AppStorage("IsDeepScheme") var IsDeepScheme = false;
    @State var colorArray:Array = [255.0,255.0,255.0]
    @State var stepperValue = 0
    @State var sliderValue = 0.0
    @State var date = Date()
    @AppStorage("UserName") var UserName:String = ""
    
    var body: some View {
        
        VStack{
            TitleView(text: "Setting")
            NavigationView{
                //TitleView(text: "Setting")
                Form(
                    content: {
                        //TitleView(text: "Setting")
                        Section(content: {
                            TextField("請輸入名字",text: $UserName)
                                .foregroundColor(tabColor()[1])
                        })
                        
                        
                        Section(header: Text("字型設定") .foregroundColor(tabColor()[1]),content: {
                            Picker(selection: $displayFontSelected, label: Text("字型選擇(\(displayFontType[displayFontSelected]))"),content: {
                                ForEach(0..<displayFontType.count, id: \.self ,content:{
                                    Text(self.displayFontType[$0])
                                     .foregroundColor(tabColor()[1])
                                })
                            })
                             .foregroundColor(tabColor()[1])
                        })
            
//                            .foregroundColor(tabColor()[1])
                        Section(header: Text("背景風格")  .foregroundColor(tabColor()[1]), content: {
                            Toggle(isOn: $IsDeepScheme, label: {
                                Text("深色\(String(IsDeepScheme))")
//                                    .foregroundColor(tabColor()[1])
                            })
                        })
                        Section(header: Text("計數器")  .foregroundColor(tabColor()[1]), content: {
                            Stepper( onIncrement: {stepperValue+=1}, onDecrement: {stepperValue-=1},
                                     label: {
                                Text("Stepper \(stepperValue)")
//                                    .foregroundColor(tabColor()[1])
                            })
                        })
                        Section(header: Text("滑桿\(sliderValue,specifier: "%.2f")")  .foregroundColor(tabColor()[1]) , content: {
                            Slider(value: $sliderValue, in: 0...1)
                                .tint(tabColor()[1])
                        })
                        //.foregroundColor(tabColor()[0])
                        Section(header: Text("日期")  .foregroundColor(tabColor()[1]), content: {
                            DatePicker("\(date.formatted(date: .numeric, time: .omitted))", selection: $date, displayedComponents: [.date])
//                                .tint(tabColor()[1])
                            
                            
                        })
                        //.background(Color(red: 245/255, green: 245/255, blue: 245/255))
                        
                    }
                )
                //.scrollContentBackground(.hidden)
                .foregroundStyle(.secondary)
               // .foregroundColor(tabColor()[0])
                //.background(tabColor()[1])
                
                //.navigationTitle("Settings 設定")
                //.navigationbarColors()
            }
            .foregroundStyle(.secondary)
            
        }
        .background(tabColor()[1])
        
    }
}

struct TitleView: View{
    @AppStorage("UserName") var UserName:String = ""
    var text:String
    var body: some View{
        HStack(spacing: 0){
            Text(UserName.isEmpty ? "" : UserName)
                .font(.system(size: 25))
                .foregroundColor(tabColor()[0])
                .background(.secondary)
                .clipShape(/*@START_MENU_TOKEN@*/Circle()/*@END_MENU_TOKEN@*/)
            Text(text)
                .font(.largeTitle)
                .fontWeight(.heavy)
                .foregroundStyle(.primary)
                .foregroundColor(tabColor()[0])
            //.listRowBackground(tabColor()[1])
            //.background(tabColor()[1])
                .frame(minWidth: 0, idealWidth: 50,maxWidth: .infinity,minHeight: 0,idealHeight: 200, alignment: .leading)
            //.padding(.leading,0)
                .fontWeight(.heavy)
            
        }
        
        
    }
}

struct TrendView: View {
    
    @State var showDetailView = false
    @State var selectCourse:Course?//value may be empty
    var body: some View {
        //
        // withIndex = courses.enumerated().map({$0})
        VStack{
            TitleView(text: "總榜")
            NavigationView{
                
                List(0..<courses.count, id:\.self){
                    index in
                    // Text()
                    BasicImageRowForTrend(thisCourse: courses[index],number: index+1)
                        .listRowBackground(tabColor()[1])
                        .listRowSeparatorTint(.white)
                        .onTapGesture {
                            //what happen will click the list
                            self.showDetailView=true
                            self.selectCourse=courses[index]
                            
                        }
                    
                    //BasicImageRow(thisRestaurant: restaurantItem)
                }
                .background(tabColor()[1])
                .scrollContentBackground(.hidden)
                .sheet(item: self.$selectCourse,content:{
                    thisCourse in
                    CourseDetailView(thisCourse: thisCourse)
                        .background(tabColor()[1])
                })
                
            }
        }
        // .background(tabColor()[1])
        .background(tabColor()[1])
        
        
        
    }
}


struct Song: Identifiable{
    var id = UUID()
    var image:String
    var SongName:String
    
}
var topSongs=[
    Song(image: "Topmix1", SongName: "Fifth Harmony, Ed Sheeran & Justin Bieber"),
    Song(image: "Topmix2", SongName: "yama, natori ,and koika"),
    Song(image: "Topmix3", SongName: "Vaundy, 10cm, Keira Knightley"),
    Song(image: "Topmix4", SongName: "Keira Knightley, 10cm and more"),
    Song(image: "Topmix5", SongName: "Backstreet Boys, Zhang Zhen Yue, Jeff Chang")
]
func tabColor()-> [Color] {
    @AppStorage("IsDeepScheme") var isDeepScheme: Bool = false
    if isDeepScheme {
        return [Color.white,Color.black]
    } else {
        return  [Color.white,Color.brown]
    }
}
struct WelcomeView: View{
    
    //    @AppStorage("IsDeepScheme") var isDeepScheme: Bool = false
    var body: some View{
        VStack{
            HStack{
                
                Text("Welcome!")
                    .font(.system(size: 20))
                    .foregroundStyle(.secondary)
                    .offset(CGSize(width: 10.0, height: 3.0))
                    .foregroundColor(tabColor()[0])
                
            }
            .frame(minWidth: 0, idealWidth: 100,maxWidth: .infinity,minHeight: 0,idealHeight: 200, alignment: .leading)
            //.padding(.leading,5)
            
            //            Image("By")
            //                .resizable()
            //                .aspectRatio(contentMode: .fill)
            //                .background(tabColor()[1])
            TitleView(text: "All")
            MusicView(SongSet: topSongs, TitleName: "Your top mixes")
            MusicView(SongSet: topSongs, TitleName: "Fresh new music")
            MusicView(SongSet: topSongs, TitleName: "Mood")
            
        }
        .background(tabColor()[1])
        
    }
}

struct MusicView: View{
    var SongSet: [Song]
    var TitleName:String
    // var isDark:Bool
    var body: some View{
        Text(TitleName)
            .foregroundColor(tabColor()[0])
            .frame(minWidth: 0, idealWidth: 100,maxWidth: .infinity, alignment: .leading)
            .padding(.leading,5)
            .fontWeight(.heavy)
        
        ScrollView(.horizontal)
        {
            HStack{
                ForEach(SongSet){
                    thisSong in
                    CardView(image: thisSong.image, SongName: thisSong.SongName)
                }
                
            }
        }
    }
}




```
 
https://youtu.be/ge4c1eWDS_4

    
  </tr>
</table>
