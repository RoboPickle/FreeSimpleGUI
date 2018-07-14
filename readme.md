
# PySimpleGUI  
  
This really is a simple GUI, but also powerfully customizable.  

![GetTextBox](https://user-images.githubusercontent.com/13696193/42592930-1ca1370a-8519-11e8-907e-ad73e9be7749.jpg)

I was frustrated by having to deal with the dos prompt when I had a powerful Windows machine right in front of me.  Why is it SO difficult to do even the simplest of input/output to a window in Python??    

With a simple GUI, it becomes practical to "associate" .py files with the python interpreter on Windows.  Double click a py file and up pops a GUI window, a more pleasant experience than opening a dos Window and typing a command line.
  
Python itself doesn't have a simple GUI solution... nor did the *many* GUI packages I tried.  Most tried to do TOO MUCH, making it impossible for users to get started quickly.  Others were just plain broken, requiring multiple files or other packages that were missing.
  
The PySimpleGUI solution is focused on the ***developer***.  How can the desired result be achieved in as little and as simple code as possible?  This was the mantra used to create PySimpleGUI. 
  
You can add a GUI to your command line with a single line of code.  With 3 or 4 lines of code you can add a fully customized GUI.  And for you Machine Learning folks out there, a **single line** progress meter call that you can drop into any loop.


![progress meter 2](https://user-images.githubusercontent.com/13696193/42695896-a37eff5c-8684-11e8-8fbb-3d756655a44b.jpg)


 The customization is via the form/dialog box builder that enables users to experience all of the normal GUI widgets without having to write a lot of code.  
  

    Features of PySimpleGUI include:  
        Text  
        Single Line Input  
        Buttons including these types:      
            File Browse
            Folder Browse
            Non-closing return
            Close form  
        Checkboxes  
        Radio Buttons  
        Icons  
        Multi-line Text Input  
        Scroll-able Output      
        Progress Bar  
        Async/Non-Blocking Windows  
        Tabbed forms
        Persistent Windows  
        Redirect Python Output/Errors to scrolling Window  
        'Higher level' APIs (e.g. MessageBox, YesNobox, ...)

  
An example of many widgets used on a single form.  A little further down you'll find the FIFTEEN lines of code required to create this complex form.

![all widgets](https://user-images.githubusercontent.com/13696193/42604818-adb1dd5c-8542-11e8-94cb-575881590f21.jpg)

  
## Getting Started with PySimpleGUI  
  
### Installing  
  
    pip install PySimpleGUI  
 or  
Simply download the file - PySimpleGUI.py and import it into your code  
  
  
### Prerequisites  
  
Python 3  
tkinter  
  
Should run on all Python platforms that have tkinter running on them.  Has been thoroughly tested on Windows.  While not tested elsewhere, should work on Linux, Mac, Pi, etc.  
  
### Using

To us in your code, simply import....
 `import PySimpleGUI as SG`  

Then use either "high level" API calls or build your own forms.  

    SG.MsgBox('This is my first message box')
![simple msgbox](https://user-images.githubusercontent.com/13696193/42597824-1749b160-8528-11e8-9114-374bf9731b30.jpg)

Yes, it's just that easy to have a window appear on the screen using Python.

## APIs
  
PySimpleGUI can be broken down into 2 types of API's:  
 * High Level single call functions  
 * Custom form functions  
   

### Python Language Features

 There are a couple of Python language features that PySimpleGUI utilizes heavily that should be understood first...
 * Variable number of arguments to a function call  
 * Optional parameters to a function call
 
#### Variable Number of Arguments

 The "High Level" API calls that *output* values take a variable number of arguments so that they match a "print" statement as much as possible.  The idea is to make it simple for the programmer to output as many items as desired and in any format.  The user need not convert the variables to be output into the strings.  The PySimpleGUI functions do that for the user.
     
    SG.MsgBox('Variable number of parameters example', my_variable, second_variable, "etc")

Each new item begins on a new line in the Message Box

  ![variablearguments](https://user-images.githubusercontent.com/13696193/42598375-022bc51e-852a-11e8-8f77-4d664ae1a560.jpg)
  
#### Optional Parameters to a Function Call
 
This feature of the Python language is utilized ***heavily*** as a method of customizing forms and part of forms.  Rather than requiring the programmer to specify every possible option for a widget, instead only the options the caller wants to override are specified.

Here is the function definition for the MsgBox function. The details aren't important.  What is important is seeing that there is a long list of potential tweaks that a caller can make.  However, they don't have to be specified on each and every call.  

    def MsgBox(*args, 
               ButtonColor=None, 
               ButtonType=MSG_BOX_OK,  
               AutoClose=False, 
               AutoCloseDuration=None, 
               Icon=DEFAULT_WINDOW_ICON, 
               LineWidth=MESSAGE_BOX_LINE_WIDTH,
               Font=None):

If the caller wanted to change the button color to be black on yellow, the call would look something like this:

    SG.MsgBox('This box has a custom button color',   
              ButtonColor=('black', 'yellow'))

![custombuttoncolor](https://user-images.githubusercontent.com/13696193/42599212-84f3fe2e-852c-11e8-8a60-4aad669a1fd6.jpg)

### High Level API Calls  

The classic "input a value, print result" example.  
Often command line programs simply take some value as input on the command line, do something with it and then display the results.  Moving from the command line to a GUI is very simple.  
This code prompts user to input a line of text and then displays that text in a messages box:  
  
    import PySimpleGUI_local as SG    
        
    rc = SG.GetTextBox('Title', 'Please input something')    
    SG.MsgBox('Results', 'The value returned from GetTextBox', rc)  
  
![GetTextBox](https://user-images.githubusercontent.com/13696193/42592930-1ca1370a-8519-11e8-907e-ad73e9be7749.jpg)  
  
![MsgBox](https://user-images.githubusercontent.com/13696193/42592929-1c7361ae-8519-11e8-8adc-411c1afee69f.jpg)  
  
#### Message Boxes
In addition to MsgBox, you'll find a several API calls that are shortcuts to common messages boxes.  You can achieve similar results by calling MsgBox with the correct parameters.

The differences tend to be the number and types of buttons.   Here are the calls and the windows that are created.

    import PySimpleGUI as SG

  `SG.MsgBoxOK('This is an OK MsgBox')`
  
  ![msgboxok](https://user-images.githubusercontent.com/13696193/42599852-8dd6914e-852e-11e8-888f-f133d787210b.jpg)

    SG.MsgBoxOKCancel('This is an OK Cancel MsgBox')

![msgboxokcancel](https://user-images.githubusercontent.com/13696193/42599858-8e8eff22-852e-11e8-8d5c-3fe99237eb7f.jpg)

    SG.MsgBoxCancel('This is a Cancel MsgBox')
![msgboxcancel](https://user-images.githubusercontent.com/13696193/42599857-8e53dc4e-852e-11e8-8e83-6a8cccf8e706.jpg)

    SG.MsgBoxYesNo('This is a Yes No MsgBox')
![msgboxyesno](https://user-images.githubusercontent.com/13696193/42599856-8e304540-852e-11e8-975d-fb2b62e94300.jpg)

    SG.MsgBoxError('This is an error MsgBox')
![msgbox error](https://user-images.githubusercontent.com/13696193/42599853-8df8e078-852e-11e8-90dc-7815d69bff7e.jpg)

    SG.MsgBoxAutoClose('This is an autoclose MsgBox')

![msgbox autoclose](https://user-images.githubusercontent.com/13696193/42599855-8e147572-852e-11e8-8c23-7ec771909062.jpg)

    SG.ScrolledTextBox(my_text, Height=10)

![scrolledtextbox](https://user-images.githubusercontent.com/13696193/42600800-a44f4562-8531-11e8-8c21-51dd70316879.jpg)

Take a moment to look at that last one.  It's such a simple API call and yet the result is awesome.  Rather than seeing text scrolling past on your display, you can capture that text and present it in a scrolled interface.  It's handy enough of an API call that it can also be called using the name `sprint` which is easier to remember than `ScrollectTextBox`. 

#### High Level User Input

There are 3 very basic user input high-level function calls.  It's expected that for most applications, a custom input form will be created. If you need only 1 value, then perhaps one of these high level functions will work.
 - GetTextBox
 - GetFileBox 
 - GetFolderBox

 `submit_clicked, value = SG.GetTextBox('Title', 'Please enter anything')`

![gettextbox](https://user-images.githubusercontent.com/13696193/42600399-1ef66a5e-8530-11e8-9bc4-78ea839213cd.jpg)

    submit_clicked, value = SG.GetFileBox('Title', 'Choose a file')

![getfilebox](https://user-images.githubusercontent.com/13696193/42600398-1ed8a122-8530-11e8-9f74-88b101efcea4.jpg)

    submit_clicked, value = SG.GetPathBox('Title', 'Choose a folder')

![getfolderbox](https://user-images.githubusercontent.com/13696193/42600397-1ea7cef8-8530-11e8-8d43-e1000c0933cd.jpg)

#### Progress Meter!
We all have loops in our code.  'Isn't it joyful waiting, watching a counter scrolling past in a text window?  How about one line of code to get a progress meter, that contains statistics about your code?
![progress meter 3](https://user-images.githubusercontent.com/13696193/42696332-dca3ca6e-8685-11e8-846b-6bee8362ee5f.jpg)

    EasyProgressMeter(Title,
                      CurrentValue,
                      MaxValue,
                      *args,
                      Orientation=None,
                      BarColor=DEFAULT_PROGRESS_BAR_COLOR,
                      ButtonColor=None,
                      Size=DEFAULT_PROGRESS_BAR_SIZE,
                      Scale=(None, None),
                      BorderWidth=DEFAULT_PROGRESS_BAR_BORDER_WIDTH):

Here's the one-line Progress Meter in action!

    for i in range(1,10000):  
        SG.EasyProgressMeter('My Meter', i+1, 1000, 'Optional message')

That line of code resulted in this window popping up and updating.

![progress meter 5](https://user-images.githubusercontent.com/13696193/42696912-a5c958b8-8687-11e8-9a7d-a390a465407a.jpg)

A meter AND fun statistics to watch while your machine grinds away, all for the price of 1 line of code.
With a little trickery you can provide a way to break out of your loop using the Progress Meter form.  The cancel button results in a `False` return value from `EasyProgressMeter`.  It normally returns `True`. 

    if not SG.EasyProgressMeter('My Meter', i+1, 10000, 'Optional message'): break

# Custom Form API Calls

This is the FUN part of the programming of this GUI.  In order to really get the most out of the API, you should be using an IDE that supports auto complete or will show you the definition of the function.  This will make customizing go  smoother.

It's both not enjoyable nor helpful to immediately jump into tweaking each and every little thing available to you.   Let's start with a basic Browse for a file and do something with it.

## COPY THIS DESIGN PATTERN!

    with SG.FlexForm('SHA-1 & 256 Hash', AutoSizeText=True) as form:  
        form_rows = [[SG.Text('SHA-1 and SHA-256 Hashes for the file')],  
                     [SG.InputText(), SG.FileBrowse()],  
                     [SG.Submit(), SG.Cancel()]]  
        (button, (source_filename, )) = form.LayoutAndShow(form_rows)

This context manager contains all of the code needed to specify, show and retrieve results for this form:
![sha hash](https://user-images.githubusercontent.com/13696193/42603149-a56acf3a-853a-11e8-91de-771efd3a65a8.jpg)

It's important to use the "with" context manager.  PySimpleGUI uses `tkinter`.  `tkinter` is very picky about who releases objects and when.  The `with` takes care of disposing of everything properly for you.

You will use this design pattern or code template for all of your "normal" (blocking) types of input forms.  Copy it and modify it to suit your needs.  This is the quickest way to get your code up and running with PySimpleGUI.  

> Copy, Paste, Run.

PySimpleGUI's goal with the API is to be easy on the programmer.  An attempt was made to make the program's code visually match the window on the screen.  The way this is done is that a GUI is broken up into "Rows".  Then each row is broke up into "Elements" or "Widgets".  Each element is specified by names such as Text, Button, Checkbox, etc. 

Some elements are shortcuts, again meant to make it easy on the programmer.  Rather than writing a `Button`, with  name = "Submit", etc, the caller simply writes `Submit`.

Going through each line of code

    with SG.FlexForm('SHA-1 & 256 Hash', AutoSizeText=True) as form:  
This creates a new form, storing it in the variable `form`.  

        form_rows = [[SG.Text('SHA-1 and SHA-256 Hashes for the file')],  
The next few rows of code lay out the rows of elements in the window to be displayed.  The variable `form_rows` holds our entire GUI window.   The first row of this form has a Text element.  These simply display text on the form.

                     [SG.InputText(), SG.FileBrowse()],  
Now we're on the second row of the form.  On this row there are 2 elements.  The first is an `Input` field.  It's a place the user can enter `strings`.  The second element is a `File Browse Button`.  A file or folder browse button will always fill in the text field to it's left unless otherwise specified.  In this example, the File Browse Button will interact with the `InputText` field to its left.

				    [SG.Submit(), SG.Cancel()]]

The last line of the `form_rows` variable assignment contains a Submit and a Cancel Button.  These are buttons that will cause a form to return its value to the caller.

        (button, (source_filename, )) = form.LayoutAndShow(form_rows)
This is the code that **displays** the form, collects the information and returns the data collected.  In this example we have a button return code and only 1 input field.

## Return values

   Return information from FlexForm, SG's primary form builder interface, is in this format:  
      
    (button, (value1, value2, ...))  
  
Don't forget all those ()'s of your values won't be coreectly assigned.  
  
If you have a SINGLE value being returned, it is written this way:  
  
    (button, (value1,)) = form.LayoutAndShow(form_rows)
 Another way of parsing the return values is to store the list of values into a variable that is then referenced.

     (button, (value)) = form.LayoutAndShow(form_rows)  
     value1 = values[0]
     value2 = values[1]
     ...
     

## All Widgets / Elements
This code utilizes as many of the elements in one form as possible.

    with FlexForm('Everything bagel', AutoSizeText=True, DefaultElementSize=(30,1)) as form:  
        layout = [[Text('Here they all are!', Size=(30,1), Font=("Helvetica", 25), TextColor='red')],  
                  [Text('Here is some text with font sizing', Font=("Helvetica", 15))],  
                  [InputText()],  
                  [Checkbox('My first checkbox!'), Checkbox('My second checkbox!', Default=True)],  
                  [Radio('My first Radio!', "RADIO1", Default=True), Radio('My second checkbox!', "RADIO1")],  
                  [Multiline(DefaultText='This is the DEFAULT text should you decide not to type anything', Scale=(2, 10))],  
                  [InputCombo(['choice 1', 'choice 2'], Size=(20, 3))],  
                  [Text('_'  * 90, Size=(60, 1))],  
                  [Text('Choose Source and Destination Folders', Size=(35,1))],  
                  [Text('Source Folder', Size=(15, 1), AutoSizeText=False), InputText('Source'), FolderBrowse()],  
                  [Text('Destination Folder', Size=(15, 1), AutoSizeText=False), InputText('Dest'), FolderBrowse()],  
                  [SimpleButton('Your Button with any text you want')],  
                  [SimpleButton('Big Text', Size=(12,1), Font=("Helvetica", 20))],  
                  [Submit(), Cancel()]]  
      
        (button, (values)) = form.LayoutAndShow(layout)




        MsgBox('Results', 'You clicked {}'.format(button),'The values returned from form', values , Font = ("Helvetica", 15))

This is a somewhat complex form with quite a bit of custom sizing to make things line up well.  This is code you only have to write once.  When looking at the code, remember that what you're seeing is a list of lists.  Each row contains a list of Graphical Elements that are used to create the form.

![all widgets](https://user-images.githubusercontent.com/13696193/42604818-adb1dd5c-8542-11e8-94cb-575881590f21.jpg)

Clicking the Submit button caused the form call to return.  The call to MsgBox resulted in this dialog box.
![results](https://user-images.githubusercontent.com/13696193/42604952-502f64e6-8543-11e8-8045-bc10d38c5fd4.jpg)

One important aspect of this example is the return codes:

    (button, (values)) = form.LayoutAndShow(layout)
The value for `button` will be the text that is displayed on the button element when it was created.  If the user closed the form using something other than a button, then `button` will be `None`.

You can see in the MsgBox that the values returned are a list.  Each input field in the form generates one item in the return values list.  All input fields return a `string` except for Check Boxes and Radio Buttons.  These return `bool`.  



# Building Custom Forms
You will find it much easier to write code using PySimpleGUI is you use features that show you documentation about the API call you are making.  In PyCharm 2 commands are helpful.

    Control-Q (when cursor is on function name) brings up a box with the function definition
    Control-P (when cursor inside function call "()") shows a list of parameters and their default values

## Synchronous Forms
The most common use of PySimpleGUI is to display and collect information from the user.  The most straightforward way to do this is using a "blocking" GUI call.  Execution is "blocked" while waiting for the user to close the GUI form/dialog box.
You've already seen a number of examples above that use blocking forms.  Anytime you see a context manager used (see the `with` statement) it's most likely a blocking form.  You can examine the show calls to be sure.  If the form is a non-blocking form, it must indicate that in the call to `form.show`.

NON-BLOCKING form call:

		    form.Show(NonBlocking=True)

### Beginning a Form
The first step is to create the form object using the desired form customization.

    with FlexForm('Everything bagel', AutoSizeText=True, DefaultElementSize=(30,1)) as form:
Let's go through the options available when creating a form.

    def __init__(self, title,
        DefaultElementSize=(DEFAULT_ELEMENT_SIZE[0], DEFAULT_ELEMENT_SIZE[1]),
        AutoSizeText=DEFAULT_AUTOSIZE_TEXT,
        Scale=(None, None),
        Size=(None, None),
        Location=(None, None),
        ButtonColor=None,Font=None,
        ProgressBarColor=(None,None),
        IsTabbedForm=False,
        BorderDepth=None,
        AutoClose=False,
        AutoCloseDuration=DEFAULT_AUTOCLOSE_TIME,
        Icon=DEFAULT_WINDOW_ICON):


#### Sizes
Note several variables that deal with "size".  Element sizes are measured in characters.  A Text Element with a size of 20,1 has a size of 20 characters wide by 1 character tall.

The default Element size for PySimpleGUI is `(45,1)`.

Sizes can be set at the element level, or in this case, the size variables apply to all elements in the form.  Setting `Size=(20,1)` in the form creation call will set all elements in the form to that size.

In addition to `size` there is a `scale` option.  Scale will take the Element's size and scale it up or down depending on the scale value.  `scale=(1,1)` doesn't change the Element's size.  `scale=(2,1)` will set the Element's size to be twice as wide as the size setting.


#### FlexForm - form-level variables overview
A summary of the variables that can be changed when a FlexForm is created

         DefaultElementSize - set default size for all elements in the form
         AutoSizeText - true/false autosizing turned on / off
         Scale - set scale value for all elements
         ButtonColor - default button color (foreground, background)
         Font - font name and size for all text items
         ProgressBarColor - progress bar colors
         IsTabbedForm - true/false indicates form is a tabbed or normal form
         BorderDepth - style setting for buttons, input fields
         AutoClose - true/false indicates if form will automatically close
         AutoCloseDuration - how long in seconds before closing form
         Icon - filename for icon that's displayed on the window on taskbar


## Elements
"Elements" are the building blocks used to create forms.  Some GUI APIs use the term Widget to describe these graphic elements.

     Text
     Single Line Input
     Buttons including these types:
         File Browse
         Folder Browse
         Non-closing return
         Close form
     Checkboxes
     Radio Buttons
     Multi-line Text Input
     Scroll-able Output
     Progress Bar
     Async/Non-Blocking Windows
     Tabbed forms
     Persistent Windows
     Redirect Python Output/Errors to scrolling Window
     "Higher level" APIs (e.g. MessageBox, YesNobox, ...)


### Output Elements
Building a form is simply making lists of Elements.  Each list is a row in the overall GUI dialog box.  The definition looks something like this:

    layout = [ [row 1 element, row 1 element],
               [row 2 element, row 2 element, row 2 element] ]
The code is a crude representation of the GUI, laid out in text.
####  Text Element

    layout = [[SG.Text('This is what a Text Element looks like')]]


 ![textelem](https://user-images.githubusercontent.com/13696193/42670173-4c1fcb40-8627-11e8-851a-5a9ee4672320.jpg)


The most basic element is the Text element.  It simply displays text.  Many of the 'options' that can be set for a Text element are shared by other elements.  Size, Scale are a couple that you will see in every element.

    Text(Text,
        Scale=(None, None),
        Size=(None, None),
        AutoSizeText=None,
        Font=None,
        TextColor=None)

Some commonly used elements have 'shorthand' versions of the functions to make the code more compact.  The functions `T` and `Txt` are the same as calling `Text`.

**Fonts** in PySimpleGUI are always in this format:

    (font_name, point_size)

The default font setting is

    ("Helvetica", 10)

**Color** in PySimpleGUI are always in this format:

    (foreground, background)

The values foreground and background can be the color names or the hex value formatted as a string:

    "#RRGGBB"

**AutoSizeText**
A `True` value for `AutoSizeText`, when placed on any Element, indicates that the width of the Element should be shrunk do the width of the text.  This is particularly useful with `Buttons` as fixed-width buttons are somewhat crude looking.  The default value is `False`.  You will often see this setting on FlexForm definitions.

**Shorthand functions**
The shorthand functions for `Text` are `Txt` and `T`


####  Multiline Text Element

    layout = [[SG.Multiline('This is what a Multi-line Text Element looks like', Size=(45,5))]]
![multiline text](https://user-images.githubusercontent.com/13696193/42670464-0824c754-8629-11e8-9741-6ed08f924618.jpg)
This Element doubles as both an input and output Element.  The `DefaultText` optional parameter is used to indicate what to output to the window.

    Multiline(DefaultText='',
			  EnterSubmits = False,
			  Scale=(None, None),
              Size=(None, None),
		      AutoSizeText=None)
.

    DefaultText - Text to display in the text box
    EnterSubmits - Bool. If True, pressing Enter key submits form
    Scale - Element's scale
    Size - Element's size
    AutoSizeText - Bool. Change width to match size of text

#### Output Element
Output re-routes `Stdout` to a scrolled text box.  It's used with Async forms.  More on this later.

    form.AddRow(gg.Output(Size=(100,20)))

![output element](https://user-images.githubusercontent.com/13696193/42704820-5446959c-869f-11e8-849e-047ea280387a.jpg)

    Output(Scale=(None, None),
           Size=(None, None))
.

     Scale - How much to scale size of element
     Size - Size of element (width, height) in characters

###  Input Elements
  These make up the majority of the form definition.  Optional variables at the Element level override the Form level values (e.g. `Size` is specified in the Element).  All input Elements create an entry in the list of return values.  A Text Input Element creates a string in the list of items returned.

#### Text Input Element

    layout = [[SG.InputText('Default text')]]
![inputtext](https://user-images.githubusercontent.com/13696193/42693515-610a716c-867d-11e8-9a00-7e7fcf771230.jpg)

      def InputText(DefaultText = '',
                    Scale=(None, None),
                    Size=(None, None),
                    AutoSizeText=None)
.

     DefaultText - Text initially shown in the input box
     Scale - Amount size is scaled by
     Size - (width, height) of element in characters
     AutoSizeText - Bool.  True is element should be sized to fit text

Shorthand functions that are equivalent to `InputText` are `Input` and `In`


#### Combo Element
Also known as a drop-down list.  Only required parameter is the list of choices.  The return value is a string matching what's visible on the GUI.

    layout = [[SG.InputCombo(['choice 1', 'choice 2'])]]

![combo](https://user-images.githubusercontent.com/13696193/42694431-631c4108-8680-11e8-8e99-c1a642734464.jpg)

    InputCombo(Values,
               Scale=(None, None),
               Size=(None, None),
               AutoSizeText=None)
.

     Values  Choices to be displayed. List of strings
     Scale - Amount to scale size by
     Size - (width, height) of element in characters
     AutoSizeText - Bool. True if size should fit the text length

#### Radio Button Element
Creates one radio button that is assigned to a group of radio buttons.  Only 1 of the buttons in the group can be selected at any one time.

    layout =  [[SG.Radio('My first Radio!', "RADIO1", Default=True), SG.Radio('My second radio!', "RADIO1")]]

![radio element](https://user-images.githubusercontent.com/13696193/42705705-327b4b6c-86a2-11e8-81a7-740e57646ba8.jpg)

     Radio(Text,
           GroupID,
           Default=False,
           Scale=(None, None),
           Size=(None, None),
           AutoSizeText=None,
           Font=None)

.

     Text - Text to display next to button
     GroupID - Groups together multiple Radio Buttons. Can be any value
     Default - Bool.  Initial state
     Scale - Amount to scale size of element
     Size - (width, height) size of element in characters
     AutoSizeText - Bool.  True if should size width to fit text
     Font - Font type and size for text display


#### Checkbox Element
Checkbox elements are like Radio Button elements.  They return a bool indicating whether or not they are checked.

    layout =  [[SG.Checkbox('My first Checkbox!', Default=True), SG.Checkbox('My second Checkbox!')]]

![checkbox element](https://user-images.githubusercontent.com/13696193/42717015-655d73d2-86cc-11e8-9c69-3c810f48e578.jpg)


    Checkbox(Text,
             Default=False,
             Scale=(None, None),
             Size=(None, None),
             AutoSizeText=None,
             Font=None):
.

     Text - Text to display next to checkbox
     Default - Bool.  Initial state
     Scale - Amount to scale size of element
     Size - (width, height) size of element in characters
     AutoSizeText - Bool.  True if should size width to fit text
     Font - Font type and size for text display


#### Spin Element
An up/down spinner control.  The valid values are passed in as a list.

    layout =  [[SG.Spin([i for i in range(1,11)], InitialValue=1), SG.Text('Volume level')]]

![spin element](https://user-images.githubusercontent.com/13696193/42717231-8ddb51d4-86cd-11e8-827a-75f2237477fa.jpg)

    Spin(Values,
         InitialValue=None,
         Scale=(None, None),
         Size=(None, None),
         AutoSizeText=None,
         Font=None)
.

     Values - List of valid values
     InitialValue - String with initial value
     Scale - Amount to scale size of element
     Size - (width, height) size of element in characters
     AutoSizeText - Bool.  True if should size width to fit text
     Font - Font type and size for text display

#### Button Element
Buttons are the most important element of all!  They cause the majority of the action to happen.  After all, it's a button press that will get you out of a form, whether it but Submit or Cancel, one way or another a button is involved in all forms.  The only exception is to this is when the user closes the window using the "X" in the upper corner which means no button was involved.

The Types of buttons include:
* Folder Browse
* File Browse
* Close Form
* Read Form


 Close Form - Normal buttons like Submit, Cancel, Yes, No, etc, are "Close Form" buttons.  They cause the input values to be read and then the form is closed, returning the values to the caller.

Folder Browse - When clicked a folder browse dialog box is opened.  The results of the Folder Browse dialog box are written into one of the input fields of the form.

File Browse - Same as the Folder Browse except rather than choosing a folder, a single file is chosen.

Read Form - This is an async form button that will read a snapshot of all of the input fields, but does not close the form after it's clicked.

While it's possible to build forms using the Button Element directly, you should never need to do that.  There are pre-made buttons and shortcuts that will make life much easier.  The most basic Button element call to use is `SimpleButton`

    SimpleButton(Text,
                 Scale=(None, None),
                 Size=(None, None),
                 AutoSizeText=None,
                 ButtonColor=None,
                 Font=None)

Pre-made buttons include:

    OK
    Ok
    Submit
    Cancel
    Yes
    No
    FileBrowse
    FolderBrowse
.
    layout =  [[SG.OK(), SG.Cancel()]]

![ok cancel](https://user-images.githubusercontent.com/13696193/42717733-1803f584-86d1-11e8-9223-36b782971b9f.jpg)

The FileBrowse and FolderBrowse buttons both fill-in values into a text input field somewhere on the form.  The location of the TextInput element is specified by the `Target` variable in the function call.  The Target is specified using a grid system.  The rows in your GUI are numbered starting with 0. The target can be specified as a hard coded grid item or it can be relative to the button.

The default value for `Target` is `(ThisRow, -1)`.   ThisRow is a special value that tells the GUI to use the same row as the button.  The Y-value of -1 means the field one value to the left of the button.  For a File or Folder Browse button, the field that it fills are generally to the left of the button is most cases.

Let's examine this form as an example:

![button target example](https://user-images.githubusercontent.com/13696193/42718075-b4dcb61e-86d3-11e8-904c-d709dd364108.jpg)

The `InputText` element is located at (1,0)... row 1, column 0.  The `Browse` button is located at position (2,0).  The Target for the button could be any of these values:

    Target = (1,0)
    Target = (-1,0)
The code for the entire form could be:

    layout =  [[SG.T('Source Folder')],
               [SG.In()],
               [SG.FolderBrowse(Target=(-1,0)), SG.OK()]]

**Custom Buttons**
If you want to define your own button, you will generally do this with the Button Element `SimpleButton`.

layout =  [[SG.SimpleButton('My Button')]]

![singlebutton](https://user-images.githubusercontent.com/13696193/42718281-9453deca-86d5-11e8-83c7-4b6d33720858.jpg)

All buttons can have their text changed by changing the `ButtonText` variable.

**File Types**
The `FileBrowse` button has an additional setting named `FileTypes`.  This variable is used to filter the files shown in the file dialog box.  The default value for this setting is

    FileTypes=(("ALL Files", "*.*"),)

This code produces a form where the Browse button only shows files of type .TXT

    layout =  [[SG.In() ,SG.FileBrowse(FileTypes=(("Text Files", "*.txt"),))]]

  ***The ENTER key***
       The ENTER key is an important part of data entry for forms.  There's a long  tradition of the enter key being used to quickly submit forms.  PySimpleGUI implements this tying the ENTER key to the first button that closes or reads a form.  If there are more than 1 button on a form, the FIRST button that is of type Close Form or Read Form is used.  First is determined by scanning the form, top to bottom and left to right.  Keep this in mind when designing forms.

#### ProgressBar
The `ProgressBar` element is used to build custom Progress Bar forms.  It is HIGHLY recommended that you use the functions that provide a complete progress meter solution for you.  Progress Meters are not easy to work with because the forms have to be non-blocking and they are tricky to debug.

The "easiest" way to get progress meters into your code is to use the `EasyProgessMeter` API.  This consists of a pair of functions, `EasyProgessMeter` and `EasyProgressMeterCancel`.  You can easily cancel any progress meter by calling it with the current value = max value.  This will mark the meter as expired and close the window.
You've already seen EasyProgressMeter calls presented earlier in this readme.

    SG.EasyProgressMeter('My Meter', i+1, 1000, 'Optional message')

If you want a bit more customization of your meter, then you can go up 1 level and use the calls to `ProgressMeter` and `ProgressMeterUpdate`

You setup the progress meter by calling

    my_meter = ProgressMeter(Title,
    					     MaxValue,
    					     *args,
    					     Orientation=None,
    					     BarColor=DEFAULT_PROGRESS_BAR_COLOR,
    					     ButtonColor=None,
    					     Size=DEFAULT_PROGRESS_BAR_SIZE,
    					     Scale=(None, None),
    					     BorderWidth=DEFAULT_PROGRESS_BAR_BORDER_WIDTH)
Then to update the bar within your loop

    return_code = ProgressMeterUpdate(my_meter,
                                     Value,
                                     *args):
Putting it all together you get this design pattern

    my_meter = SG.ProgressMeter('Meter Title', 100000, Orientation='Vert')

    for i in range(0, 100000):
        SG.ProgressMeterUpdate(my_meter, i+1, 'Some variable', 'Another variable')

The final way of using a Progress Meter with PySimpleGUI is to build a custom form with a `ProgressBar` Element in the form.  You will need to run your form as a non-blocking form.  When you are ready to update your progress bar, you call the `UpdateBar` method for the `ProgressBar` element itself.


#### Output
The Output Element is a re-direction of Stdout.  Anything "printed" will be displayed in this element.

    Output(Scale=(None, None),
           Size=(None, None))

Here's a complete solution for a chat-window using an Async form with an Output Element

    import PySimpleGUI as g

    with g.FlexForm('Chat Window', AutoSizeText=True, DefaultElementSize=(30, 2)) as form:
        form.AddRow(g.Text('This is where standard out is being routed', Size=[40,1]))
        form.AddRow(g.Output(Size=(80, 20)))
        form.AddRow(g.Multiline(Size=(70, 5), EnterSubmits=True), g.ReadFormButton('SEND', ButtonColor=(g.YELLOWS[0], g.BLUES[0])), g.SimpleButton('EXIT', ButtonColor=(g.YELLOWS[0], g.GREENS[0])))

        # ---===--- Loop taking in user input and printing it --- #
      while True:
            (button, value) = form.Read()
            if button == 'SEND':
                print(value)
            else:
                print('Exiting the form now')
                break


#### Tabbed Forms
Tabbed forms are shown using the `ShowTabbedForm` call.  The call has the format

     results = ShowTabbedForm('Title for the form',
                              (form,layout,'Tab 1 label'),
                              (form2,layout2, 'Tab 2 label'))

Each of the tabs of the form is in fact a form.  The same steps are taken to create the form as before.  A `FlexForm` is created, then rows are filled with Elements, and finally the form is shown.  When calling `ShowTabbedForm`, each form is passed in as a tuple.  The tuple has  the format:  `(the form, the rows, a label shown on the tab)`

## Asynchronous (Non-Blocking) Forms


## Contributing

A MikeTheWatchGuy production... entirely responsible for this code

## Versioning

1.0.9  -   July 10, 2018 - Initial Release
1.0.21 - July 13, 2018 - Readme updates

  ## Code Condition

    Make it run
    Make it right
    Make it fast

It's a recipe for success if done right.  PySimpleGUI has completed the "Make it run" phase.  It's far from "right" in many ways.  These are being worked on.  The module is particularly poor on hiding implementation details, naming conventions, PEP 8.  It was a learning exercise that turned into a somewhat complete GUI solution for lightweight problems.

## Authors


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Jorj McKie was the motivator behind the entire project. His wxsimpleGUI concepts sparked PySimpleGUI into existence


