Hier ist ein einfaches Beispiel für eine ContentView, in der die AutoCompleteTextField eingebettet wird. 

In dieser Ansicht werden einige Beispielvorschläge angezeigt, und sobald ein Vorschlag ausgewählt wird, wird der ausgewählte Text in der Benutzeroberfläche dargestellt.

```swift
import SwiftUI
struct ContentView: View {
    @State private var selectedSuggestion: String = ""
    
    let suggestions = ["Apple", "Banana", "Orange", "Peach", "Grape", "Watermelon", "Mango", "Blueberry", "Strawberry"]
    
    var body: some View {
        VStack(spacing: 20) {
            Text("Autocomplete TextField Example")
                .font(.title)
            
            // AutoCompleteTextField embedded
            AutoCompleteTextField(suggestions: suggestions) { selected in
                // Action on selecting a suggestion
                selectedSuggestion = selected
            }
            .padding(.horizontal)
            
            // Display the selected suggestion below the TextField
            if !selectedSuggestion.isEmpty {
                Text("Selected Suggestion: \(selectedSuggestion)")
                    .padding()
                    .background(Color.gray.opacity(0.2))
                    .cornerRadius(5)
            }
            
            Spacer()
        }
        .padding()
    }
}
struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}
´´
