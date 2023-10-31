from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.textinput import TextInput
from kivy.uix.button import Button
from kivy.uix.label import Label

class ToDoApp(App):
    def build(self):
        self.tasks = []  # List to store tasks
        self.layout = BoxLayout(orientation='vertical')
        
        self.task_input = TextInput(hint_text='Enter a task')
        self.add_task_button = Button(text='Add Task')
        self.add_task_button.bind(on_press=self.add_task)
        
        self.task_list = BoxLayout(orientation='vertical')
        
        self.layout.add_widget(self.task_input)
        self.layout.add_widget(self.add_task_button)
        self.layout.add_widget(self.task_list)
        
        return self.layout

    def add_task(self, instance):
        task_text = self.task_input.text
        if task_text:
            self.tasks.append(task_text)
            task_label = Label(text=task_text)
            self.task_list.add_widget(task_label)
            self.task_input.text = ''  # Clear the input field

if __name__ == '__main__':
    ToDoApp().run()
