# Music-app

import pygame
import os

pygame.mixer.init()

def play_music(file_path):
    if not os.path.isfile(file_path):
        print("File does not exist. Please check the path.")
        return

    pygame.mixer.music.load(file_path)
    pygame.mixer.music.play()
    print("Playing:", file_path)

def stop_music():
    pygame.mixer.music.stop()
    print("Music stopped")

def main():
    print("Simple Music Player")

    music_directory = input("Enter the path to your music directory: ").strip('"')

    music_files = [file for file in os.listdir(music_directory) if file.endswith(('.mp3', '.wav'))]

    if not music_files:
        print("No music files found in the directory.")
        return

    print("\nAvailable music files:")
    for index, file in enumerate(music_files):
        print(f"{index + 1}. {file}")

    while True:
        print("\nOptions:")
        print("1. Play a music file")
        print("2. Stop music")
        print("3. Exit")

        choice = int(input("Enter your choice (1/2/3): "))

        if choice == 1:
            file_choice = int(input("Enter the number of the file to play: ")) - 1
            if 0 <= file_choice < len(music_files):
                file_path = os.path.join(music_directory, music_files[file_choice])
                play_music(file_path)
            else:
                print("Invalid choice")
        elif choice == 2:
            stop_music()
        elif choice == 3:
            stop_music()
            break
        else:
            print("Invalid input. Please enter a number between 1 and 3.")

if __name__ == "__main__":
    main()
