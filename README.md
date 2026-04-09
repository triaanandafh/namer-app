# Laporan Tugas Praktikum Pemrograman Mobile - Week 05
**Nama**: Tria Ananda  
**NIM**: 244107060149  
**Kelas**: SIB 2G  

---

## 📱 Prakticum 1: Create a project

**Steps:**
1. Launch Visual Studio Code and open the command palette (with F1 or Ctrl+Shift+P or Shift+Cmd+P). Start typing "flutter new". Select the Flutter: New Project command.
2. Next, select Application and then a folder in which to create your project. This could be your home directory, or something like C:\src\.
> ![Capture HP](images/01-bagian1.png)
3. In the left pane of VS Code, make sure that Explorer is selected, and open the pubspec.yaml file. Replace the contents of this file with the following:
> ![Capture HP](images/02-bagian1.png)
4. Next, open another configuration file in the project, analysis_options.yaml. Replace its contents with the following:
> ![Capture HP](images/03-bagian1.png)
5. Finally, open the main.dart file under the lib/ directory. Replace the contents of this file with the following:
> ![Capture HP](images/04-bagian1.png)

---

## 📱 Prakticum 2: Add a button
This step adds a Next button to generate a new word pairing.

**Steps:**
1. Next, add a button at the bottom of the Column, right below the second Text instance.
2. When you save the change, the app updates again: A button appears and, when you click it, the Debug Console in VS Code shows a button pressed! message.
> ![Capture HP](images/01-bagian2.png)
3. Scroll to MyAppState and add a getNext method. 
> ![Capture HP](images/02-bagian2.png)
4. Save and try the app now. It should generate a new random word pair every time you press the Next button.
> ![Capture HP](images/03-bagian2.gif)

---

## 📱 Make the app prettier
This section addresses these issues by working on the app's design. 

**Steps:**
1. For extract widget, rewrite the MyHomePage widget as follows:
> ![Capture HP](images/01-bagian3.png)
2. Now, call up the Refactor menu. Move your cursor to the piece code you want to refactor (Text, in this case), and press Ctrl+. In the Refactor menu, select Extract Widget. Assign a name, such as BigCard, and click Enter.
> ![Capture HP](images/02-bagian3.png)
This automatically creates a new class, BigCard, at the end of the current file. The class looks something like the following:
> ![Capture HP](images/03-bagian3.png)
3. Find the BigCard class and the build() method within it. As before, call up the Refactor menu on the Text widget. However, this time you aren't going to extract the widget. Instead, select Wrap with Padding. This creates a new parent widget around the Text widget called Padding
> ![Capture HP](images/04-bagian3.png)
> ![Capture HP](images/05-bagian3.png)
4. Save and try the app now. It should generate a new random word pair every time you press the Next button.
> ![Capture HP](images/03-bagian2.gif)
5. Next, go one level higher. Place your cursor on the Padding widget, pull up the Refactor menu, and select Wrap with widget. Type "Card" and press Enter. This wraps the Padding widget, and therefore also the Text, with a Card widget.
> ![Capture HP](images/06-bagian3.png)
> ![Capture HP](images/07-bagian3.png)
> ![Capture HP](images/08-bagian3.png)
6. To make the card stand out more, paint it with a richer color. And because it's always a good idea to keep a consistent color scheme, use the app's Theme to choose the color
> ![Capture HP](images/09-bagian3.png)
7. For TextTheme, The card still has a problem: the text is too small and its color is hard to read. To fix this, make the following changes to BigCard's build() method.
> ![Capture HP](images/10-bagian3.png)
8. To keep the visual simplicity of pair.asLowerCase. Use Text's semanticsLabel property to override the visual content of the text widget with a semantic content that is more appropriate for screen readers:
> ![Capture HP](images/11-bagian3.png)
9. To center the UI, go to MyHomePage's build() method, and make the following change:
> ![Capture HP](images/12-bagian3.png)
> ![Capture HP](images/13-bagian3.png)
10. The children are already centered along the column's cross axis (in other words, they are already centered horizontally). But the Column itself isn't centered inside the Scaffold. We can verify this by using the Widget Inspector.
You can just center the column itself. Put your cursor onto Column, call up the Refactor menu (with Ctrl+. or Cmd+.), and select Wrap with Center.
> ![Capture HP](images/14-bagian3.png)
> ![Capture HP](images/15-bagian3.png)
11. You can remove the Text widget above BigCard. It could be argued that the descriptive text ("A random AWESOME idea:") isn't needed anymore. You can also add a SizedBox(height: 10) widget between BigCard and ElevatedButton.
> ![Capture HP](images/16-bagian3.png)
And the app looks like the following:
> ![Capture HP](images/17-bagian3.png)

## 📱 Add Functionality

**Steps:**
1. Scroll to MyAppState and add the following code:
> ![Capture HP](images/01-bagian4.png)
2. With the "business logic" out of the way, it's time to work on the user interface again. Placing the ‘Like' button to the left of the ‘Next' button requires a Row. The Row widget is the horizontal equivalent of Column, which you saw earlier.
First, wrap the existing button in a Row. Go to MyHomePage's build() method, put your cursor on the ElevatedButton, call up the Refactor menu with Ctrl+. or Cmd+., and select Wrap with Row.
> ![Capture HP](images/02-bagian4.png)
When you save, you'll notice that Row acts similarly to Column—by default, it lumps its children to the left. To fix this, you could use the same approach as before, but with mainAxisAlignment.
> ![Capture HP](images/03-bagian4.png)
> ![Capture HP](images/04-bagian4.png)
The UI is back to where it was before.
> ![Capture HP](images/05-bagian4.png)
3. Next, add the Like button and connect it to toggleFavorite(). This time, use the ElevatedButton.icon() constructor to create a button with an icon. And at the top of the build method, choose the appropriate icon depending on whether the current word pair is already in favorites. Also, note the use of SizedBox again, to keep the two buttons a bit apart.
> ![Capture HP](images/06-bagian4.png)
4. The app should look as follows:
> ![Capture HP](images/07-bagian4.png)

---

## 📱 Add navigation rail
Most apps can't fit everything into a single screen. This particular app probably could, but for didactic purposes, you are going to create a separate screen for the user's favorites. To switch between the two screens, you are going to implement your first StatefulWidget.

**Steps:**
1. To get to the meat of this step as soon as possible, split MyHomePage into 2 separate widgets.
Select all of MyHomePage, delete it, and replace with the following code:
2. When you save the change, the app updates again: A button appears and, when you click it, the Debug Console in VS Code shows a button pressed! message.
> ![Capture HP](images/01-bagian5.png)
3. Place your cursor on the first line of MyHomePage (the one that starts with class MyHomePage...), and call up the Refactor menu using Ctrl+. or Cmd+.. Then, select Convert to StatefulWidget.
> ![Capture HP](images/02-bagian5.png)
4. The new stateful widget only needs to track one variable: selectedIndex. Make the following 3 changes to _MyHomePageState:
> ![Capture HP](images/03-bagian5.png)

---