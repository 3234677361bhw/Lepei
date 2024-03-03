import datetime
import time
import winsound

def set_alarm(alarm_time, thing):
    while True:
        current_time = datetime.datetime.now().strftime("%H:%M:%S")
        if current_time == alarm_time:
            print(current_time, thing)
            for i in range(5):  # 响铃5次
                winsound.Beep(1000, 1000)  # 发出响铃声
                time.sleep(1)
            break
        time.sleep(1)

def read_alarm_from_file(file_path):
    with open(file_path, 'r', encoding='utf-8') as file:
        lines = file.readlines()
        for line in lines:
            parts = line.strip().split(',')
            if len(parts) == 2:
                alarm_time = parts[0]
                thing = parts[1]
                set_alarm(alarm_time, thing)

if __name__ == "__main__":
    file_path = 'result.txt'  # 替换为实际的文件路径
    read_alarm_from_file(file_path)
