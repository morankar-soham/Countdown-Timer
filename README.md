# Countdown-Timer
Countdown timer application in Python. The user should be able to set a specific countdown duration in minutes or seconds. When the timer ends, the app should alert the user with a notification or print a message to the console. Utilize Python's time and threading modules to manage the countdown and timing.
import time
import threading
import winsound  # For Windows sound notification

def countdown_timer(seconds):
    while seconds:
        mins, secs = divmod(seconds, 60)
        print(f"Time left: {mins:02}:{secs:02}", end="\r")
        time.sleep(1)
        seconds -= 1
    
    print("\nTime's up! 🚀")
    winsound.Beep(1000, 1000)  # Play a beep sound (Windows only)

def main():
    try:
        duration = int(input("Enter countdown duration in seconds: "))
        timer_thread = threading.Thread(target=countdown_timer, args=(duration,))
        timer_thread.start()
        timer_thread.join()
    except ValueError:
        print("Please enter a valid number.")

if __name__ == "__main__":
    main()


