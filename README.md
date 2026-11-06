import re

def validate_email(email):
    email = email.strip()

    pattern = (
        r"^[a-zA-Z0-9._%+-]+"
        r"@[a-zA-Z0-9.-]+"
        r"\.[a-zA-Z]{2,}$"
    )

    if not email:
        return False, "Email cannot be empty."

    if " " in email:
        return False, "Email cannot contain spaces."

    if email.count("@") != 1:
        return False, "Email must contain exactly one @."

    if not re.match(pattern, email):
        return False, "Invalid email format."

    return True, "Email format is valid."

def main():
    print("===== EMAIL VALIDATOR =====")

    while True:
        email = input("\nEnter email (or 'exit'): ")

        if email.lower() == "exit":
            break

        valid, message = validate_email(email)

        if valid:
            print("[VALID]", message)
        else:
            print("[INVALID]", message)

if __name__ == "__main__":
    main()
