import re

def check_password_strength(password):
    """Checks the strength of a password and returns a strength level."""

    length = len(password)
    has_uppercase = re.search("[A-Z]", password) is not None
    has_lowercase = re.search("[a-z]", password) is not None
    has_numbers = re.search("[0-9]", password) is not None
    has_symbols = re.search("[^a-zA-Z0-9]", password) is not None

    score = 0
    if length >= 8:
        score += 1
    if has_uppercase:
        score += 1
    if has_lowercase:
        score += 1
    if has_numbers:
        score += 1
    if has_symbols:
        score += 1

    if score <= 2:
        strength = "Weak"
    elif score == 3 or score == 4:
        strength = "Medium"
    elif score == 5:
        strength = "Strong"
    else:
        strength = "Very Strong"

    return strength


if __name__ == "__main__":
    password = input("Enter password: ")
    strength = check_password_strength(password)
    print(f"Password strength: {strength}")

