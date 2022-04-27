# TermuxCreate
Template for creating terminal based scripts in python.

---USAGE---

/ Import termuxcreate

import TermuxCreate as tc


/ Action to run

def print_input(msg):
    print(msg)


/ You add the commands you want to use 

tc.add_command(command='testcommand', arguments=1, cmdinfo="[+] prints whatever u type.", action=print_input)
    | command /  We set a command name whenever we type it this name will be used to access the function.
    | arguments / We input a number of required arguments for a function 
    | action / Function to call when success of this command.

/ We create a function to get input

def terminal():
    while 1:
        input_ = input("shell> ")
        command = input_.split()
        if command:
            cmd_result, msg = tc.cmd_result(command=command[0], input_=input_)  # we use 0 to get the command name
            if not cmd_result:
                print(msg)
    |  def terminal() / we can create an loop to get input forever to feed the terminal input.
    |  command = input_.split() / this is the full command along with arguments passed, we need to supply this to tc.cmd_result()
    |  cmd_result, msg = tc.cmd_result(command=command[0], input_=input_)/ tc.cmd_result() returns two values which are either 'True' or 'False' and if the command passed the arg check and the error msg if it did not pass.
    |  if command: / We use this in order to prevent no input from passing through.
    |  if not cmd_result: print(msg) / this means if the command result turns out to be false print the error message.
