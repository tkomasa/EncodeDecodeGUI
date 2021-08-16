# Imports
from tkinter import *
from tkinter.ttk import Combobox
import base64

# Setting up window
root = Tk()
root.geometry('500x300')
root.resizable(0, 0)
root.title("tkomasa's Encrypt & Decrypt App")
Label(root, text='ENCODE DECODE', font='arial 20 bold').pack()
Label(root, text='TKomasa GitHub.', font='arial 10 bold').pack(side='bottom')

# Defining vars
text = StringVar()
private_key = StringVar()
mode = StringVar()
result = StringVar()
options = ['Encrypt', 'Decrypt']


# Encrypt function
def encode(key, message):
    enc = []
    for i in range(len(message)):
        key_c = key[i % len(key)]
        enc.append(chr((ord(message[i]) + ord(key_c)) % 256))
    return base64.urlsafe_b64encode("".join(enc).encode()).decode()


# Decrypt function
def decode(key, message):
    dec = []
    message = base64.urlsafe_b64decode(message).decode()
    for i in range(len(message)):
        key_c = key[i % len(key)]
        dec.append(chr((256 + ord(message[i]) - ord(key_c)) % 256))
    return "".join(dec)


# Set mode: decrypt or encrypt
def Mode():
    if mode.get() == 'Encrypt':
        result.set(encode(private_key.get(), text.get()))
    elif mode.get() == 'Decrypt':
        result.set(decode(private_key.get(), text.get()))
    else:
        result.set('Invalid Mode')


# Exit
def Exit():
    root.destroy()


# Reset
def Reset():
    text.set("")
    private_key.set("")
    mode.set("")
    result.set("")


# Window entries, buttons, layout, and loop
Label(root, font='arial 12 bold', text='MESSAGE').place(x=60, y=60)
Entry(root, font='arial 10', textvariable=text, bg='ghost white').place(x=290, y=60)

Label(root, font='arial 12 bold', text='KEY').place(x=60, y=90)
Entry(root, font='arial 10', textvariable=private_key, bg='ghost white').place(x=290, y=90)

# this is where the option menu goes if i can figure it out
Label(root, font='arial 12 bold', text='MODE').place(x=60, y=120)
mode.set('Encrypt')  # default value
Combobox(root, values=options).place(x=290, y=120)

Button(root, font='arial 10 bold', text='RESULT', padx=2, bg='LightGray', command=Mode).place(x=60, y=150)

Button(root, font='arial 10 bold', text='RESET', width=6, command=Reset, bg='LimeGreen', padx=2).place(x=170, y=220)

Button(root, font='arial 10 bold', text='EXIT', width=6, command=Exit, bg='Red', padx=2, pady=2).place(x=270,
                                                                                                       y=220)
root.mainloop()
