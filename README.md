# pyproject
Made an attendance tracking system!



import math

def calculate_required_classes(name, attended, total_classes, target_percent):
    if total_classes == 0:
        print("\nYou haven't attended any classes yet.")
        return

    if not (0 < target_percent <= 100):
        print("\nTarget attendance must be between 1 and 100.")
        return

    current_percent = (attended / total_classes) * 100
    print(f"\n{name}, your current attendance is: {current_percent:.2f}%")

    if current_percent >= target_percent:
        print(f"You already meet or exceed the target of {target_percent}%. Great job!")
        return

    # Formula derived from:
    # (attended + x) / (total_classes + x) >= target_percent / 100
    p = target_percent / 100
    x = math.ceil((p * total_classes - attended) / (1 - p))

    print(f"To reach {target_percent}%, you need to attend the next {x} classes consecutively without missing any.\n")

# --- User Input Section (using exception handling)

try:
    print("HAHA!! ITS NOW TIME TO FIX YOUR ATTENDANCE!! LETS GET GOING!!\n")

    name = input("Enter your name: ").strip()
    total_classes = int(input("Enter total number of classes conducted: "))
    attended = int(input("Enter number of classes you have attended: "))
    target_percent = float(input("Enter your target attendance percentage (e.g., 75): "))

    calculate_required_classes(name, attended, total_classes, target_percent)

except ValueError:
    print("\n❌ Please enter valid numeric input for classes and percentage.")
