# Chatbot using python
import tkinter as tk

responses = {
    "hello": "Hi, Welcome! How can I help you?",
    "how are you": "I am fine, thank you.",
    "who are you": "I am a chatbot.",
    "motivate me": "Keep going, you are doing good!",
    "default": "Sorry, I did not understand your question."
}

def get_response(user_question):
    user_question = user_question.lower()

    for key in responses:
        if key in user_question:
            return responses[key]

    return responses["default"]

def send_message():
    user_message = entry.get()

    chat_box.insert(tk.END, "You: " + user_message + "\n")

    bot_reply = get_response(user_message)

    chat_box.insert(tk.END, "Bot: " + bot_reply + "\n\n")

    entry.delete(0, tk.END)

#  Window
root = tk.Tk()
root.title("My Chatbot")
root.geometry("500x500")

# Chat
chat_box = tk.Text(root, height=20, width=55)
chat_box.pack(pady=10)

# Input
entry = tk.Entry(root, width=40)
entry.pack(side=tk.LEFT, padx=10)

# Send
send_button = tk.Button(root, text="Send", command=send_message)
send_button.pack(side=tk.LEFT)

root.mainloop()
