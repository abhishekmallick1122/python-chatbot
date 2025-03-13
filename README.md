# python-chatbot
import tkinter as tk
from tkinter import scrolledtext, ttk, Frame, Label, Entry, Button

# Predefined responses
responses = {
    "hello": "Hello! How can I help you  ?",
    "how are you": "I'm just a bot, but I'm doing great! How about you?",
    "what is your name": "I'm a simple chatbot created in Python.",
    "bye": "Goodbye! Have a great day!",
    "default": "I'm sorry, I don't understand that. Can you rephrase?",
            "bye": "Goodbye! Have a great day!",
            "goodbye": "Goodbye! Have a great day!",
            "how are you": "I'm just a program, but I'm here to help you. How can I assist you?",
            "what is your name": "I'm an AI chatbot created to assist you. What's your name?",
            "weather": "I can't check the weather, but it's always a good idea to carry an umbrella just in case!",
            "joke": "Why don't scientists trust atoms? Because they make up everything!",
            "favorite color": "I don't have a favorite color, but I think all colors are beautiful!",
            "time": "I can't tell the time, but it's always a good moment to chat with you.",
            "food": "I don't eat, but I hear pizza is a universal favorite!",
            "hobby": "I enjoy helping you with your questions. What's your hobby?",
            "how do you work?":	"I'm powered by advanced AI technology created by Microsoft to assist you.",
            "what's the meaning of life?":"That's a big question! Some say it's to find happiness and make a difference. What do you think?",
            "can you help me with my homework?":	"Absolutely! What subject or topic do you need help with?",
            "are you alive?	I'm not alive": "I'm a program designed to help you with information and tasks.",
            "do you have friends?":	"I don't have friends like humans do, but I enjoy interacting with you!",
            "can you dance":	"I can't dance, but I'd love to see your moves!",
            "what's the best way to cook [dish]?":	"I can share a recipe for [dish] if you'd like!",
            "can you play games ":	"I can't play games, but I can share tips and strategies for your favorite games!",
            "hi": "Hello! How can I help you today ,I am your python tutor so feel free to ask questions?",
            
            "hey": "Hey! What's up?",
            "good morning": "Good morning! How's your day starting?",
            "good afternoon": "Good afternoon! How can I assist you today?",
            "good evening": "Good evening! What can I do for you?",
            
            "how's it going?": "All systems are go! How can I assist you?",
            "what's up": "Not much, just here to help. What's up with you?",
            "greetings": "Greetings! How may I assist you today?",
            "hi there": "Hello! How can I make your day better?",
            "what's new?": "Just here, ready to help. What's new with you?",
            "how do you do?": "I'm doing well, thanks! How can I assist you today?",
            "how have you been?": "I've been here, ready to assist you. How about you?",
            "Its nice to meet you": "It's nice to meet you too! How can I assist you?",
            "long time no see": "Indeed! How have you been?",
                        
            
            "python": "Python is a popular programming language known for its readability and versatility.",  "variable": "You can declare a variable in Python by simply assigning a value to it. For example: `x = 5`.",
            "lists": "Lists are ordered collections of items in Python. They are defined using square brackets. For example: `my_list = [1, 2, 3]`.",
            "function": "You can create a function in Python using the `def` keyword. For example:\n```\ndef my_function():\n print('Hello, World!')\n```", 
            "dictionary": "A dictionary is a collection of key-value pairs in Python. They are defined using curly braces. For example: `my_dict = {'key1': 'value1', 'key2': 'value2'}`.",
            "handle exceptions": "Exceptions in Python can be handled using try-except blocks. For example:\n```\ntry:\n # code that might raise an exception\nexcept SomeException as e:\n # code that runs if an exception occurs\n```",
            "class": "A class in Python is a blueprint for creating objects. It allows you to bundle data and functionality together. For example:\n```\nclass MyClass:\n def __init__(self, name):\n self.name = name\n def greet(self):\n print(f'Hello, {self.name}!')\n```", 
            "file": "You can read a file in Python using the `open()` function. For example:\n```\nwith open('file.txt', 'r') as file:\n content = file.read()\n print(content)\n```", 
            "modules": "Modules in Python are files containing Python code that can be imported and used in other Python programs. For example, you can import the `math` module using `import math`.",
            "lambda function": "A lambda function is an anonymous function defined using the `lambda` keyword. For example: `square = lambda x: x * x`.",
            "install packages": "You can install packages in Python using the `pip` command. For example: `pip install package_name`.",
            "string to integer": "You can convert a string to an integer in Python using the `int()` function. For example: `num = int('123')`.", 
            "tuple": "A tuple is an immutable ordered collection of items in Python. They are defined using parentheses. For example: `my_tuple = (1, 2, 3)`.", 
            "list comprehension": "List comprehensions provide a concise way to create lists. For example: `[x * x for x in range(5)]` creates a list of squares of numbers from 0 to 4.", 
            "iterator": "An iterator is an object that allows you to traverse through all the elements of a collection. It implements the `__iter__()` and `__next__()` methods.",
            "generator": "You can create a generator in Python using the `yield` keyword. For example:\n```\ndef my_generator():\n yield 1\n yield 2\n yield 3\n```",
            "decorator": "A decorator is a function that takes another function as an argument and extends its behavior without modifying it. They are defined using the `@` symbol.", 
            "merge dictionaries": "You can merge two dictionaries in Python using the `update()` method. For example: `dict1.update(dict2)`.",
            " *args and **kwargs": "`*args` and `**kwargs` allow you to pass a variable number of arguments to a function. `*args` is used for non-keyword arguments, and `**kwargs` is used for keyword arguments.", 
            "PEP 8": "PEP 8 is the Python Enhancement Proposal which provides guidelines and best practices on how to write Python code.", 
            "comment": "You can make a comment in Python by starting the line with the `#` character. For example: `# This is a comment`.", 
            "length of a list": "You can get the length of a list in Python using the `len()` function. For example: `len(my_list)`.", 
            "append": "You can append an item to a list in Python using the `append()` method. For example: `my_list.append(item)`.",
            "can do":"I can help you to understand  python basic concept ",
            "created you":"I am created by Abhishek Mallick^_^ ,Aditya raj^_~ and Neha Prajapati(❁´◡`❁)",
            "who are you":"I am a AI-Python tutor ,here to help you "
}

# Suggested questions/actions
suggestions = [
    "about python",
    "Ask how I am",
    "Ask my name",
    "Say goodbye",
    "Variables",

    "DataTypes",
    
    "Operators",
    
    "Strings",
    
    "Lists",
    
    "Tuples",
    
    "Dictionaries",
    
    "Sets",
    
    "Conditionals",
    
    "Loops",
    
    "Functions",
    
    "Modules",
    
    "Exceptions",
    
    "FileHandling",
    
    "Classes",

    "Objects"
]

# Function to get a response from the bot
def get_response(user_input):
    user_input = user_input.lower()
    for key in responses:
        if key in user_input:
            return responses[key]
    return responses["default"]

# Function to handle sending messages
def send_message():
    user_input = user_entry.get()
    if user_input.strip() == "":
        return
    add_message("You: " + user_input, "user")
    add_message("Bot: " + get_response(user_input), "bot")
    user_entry.delete(0, tk.END)
    chat_area.yview(tk.END)

# Function to add a message to the chat area
def add_message(text, sender):
    chat_area.config(state=tk.NORMAL)
    if sender == "user":
        chat_area.insert(tk.END, text + "\n", "user")
    else:
        chat_area.insert(tk.END, text + "\n", "bot")
    chat_area.config(state=tk.DISABLED)

# Function to handle suggestion selection
def use_suggestion(event):
    selected_suggestion = suggestion_box.get()
    user_entry.delete(0, tk.END)
    user_entry.insert(0, selected_suggestion)

# Function to display a greeting message when the app starts
def show_greeting():
    add_message("Bot: Hi there! Welcome to the chatbot. How can I assist you today(^///^)?", "bot")

# Create the main window
root = tk.Tk()
root.title("AI-Python tutor")
root.geometry("400x600")
root.configure(bg="#121212")  # Dark background

# Create a scrolled text area for the chat
chat_area = scrolledtext.ScrolledText(root, wrap=tk.WORD, state=tk.DISABLED, font=("Helvetica", 12), bg="#121212", fg="#FFFFFF", padx=10, pady=10)
chat_area.pack(padx=10, pady=10, fill=tk.BOTH, expand=True)

# Configure tags for user and bot messages (borderless)
chat_area.tag_config("user", foreground="#FFFFFF", background="#333333", justify="right", lmargin1=100, lmargin2=100, rmargin=10, spacing3=5)
chat_area.tag_config("bot", foreground="#FFFFFF", background="#444444", justify="left", lmargin1=10, lmargin2=10, rmargin=100, spacing3=5)

# Create a frame for the input area
input_frame = Frame(root, bg="#121212")
input_frame.pack(padx=10, pady=10, fill=tk.X)

# Create an entry field for user input
user_entry = Entry(input_frame, width=30, font=("Helvetica", 12), relief=tk.FLAT, bg="#333333", fg="#FFFFFF", insertbackground="#FFFFFF", highlightthickness=1, highlightbackground="#555555", highlightcolor="#34B7F1")
user_entry.pack(side=tk.LEFT, padx=5, fill=tk.X, expand=True, ipady=5)

# Create a send button
send_button = Button(input_frame, text="Send", command=send_message, bg="#34B7F1", fg="#FFFFFF", font=("Helvetica", 12, "bold"), relief=tk.FLAT, activebackground="#2A9FD8", activeforeground="#FFFFFF")
send_button.pack(side=tk.RIGHT, padx=5, ipady=5)

# Create a suggestion box
suggestion_label = Label(root, text="Suggestions:", bg="#121212", font=("Helvetica", 12, "bold"), fg="#FFFFFF")
suggestion_label.pack(padx=10, pady=(10, 0), anchor=tk.W)

suggestion_box = ttk.Combobox(root, values=suggestions, font=("Helvetica", 12), state="readonly", background="#333333", foreground="#FFFFFF")
suggestion_box.pack(padx=10, pady=(0, 10), fill=tk.X, ipady=5)
suggestion_box.bind("<<ComboboxSelected>>", use_suggestion)

# Bind the Enter key to send the message
root.bind('<Return>', lambda event: send_message())

# Show greeting message when the app starts
show_greeting()

# Start the main loop
root.mainloop()
