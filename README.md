- 👋 Hi, I’m @1213213424
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
1213213424/1213213424 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import tkinter as tk
from tkinter import messagebox
import time

class TimeManagerApp:
    def __init__(self, root):
        self.root = root
        self.root.title("時間管理應用程式")
        
        self.label = tk.Label(root, text="選擇您要計時的時間（以分鐘為單位）：")
        self.label.pack()
        
        self.entry = tk.Entry(root)
        self.entry.pack()
        
        self.start_button = tk.Button(root, text="開始計時", command=self.start_timer)
        self.start_button.pack()
        
    def start_timer(self):
        try:
            minutes = int(self.entry.get())
            seconds = minutes * 60
            
            while seconds >= 0:
                minutes, secs = divmod(seconds, 60)
                time_format = '{:02d}:{:02d}'.format(minutes, secs)
                print(time_format)  # 在控制台中顯示計時器
                self.root.update()  # 更新圖形用戶界面
                time.sleep(1)  # 暫停1秒
                seconds -= 1
            
            messagebox.showinfo("時間到！", "時間已經用完！")
        except ValueError:
            messagebox.showerror("錯誤", "請輸入有效的數字！")

# 建立應用程式窗口
root = tk.Tk()

# 建立時間管理應用程式
app = TimeManagerApp(root)

# 開始主迴圈
root.mainloop()

