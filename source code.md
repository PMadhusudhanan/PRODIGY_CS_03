    import re

    def assess_password_strength(password):

    length_weight = 2
    upper_weight = 1
    lower_weight = 1
    digit_weight = 1
    special_weight = 2


    score = 0


    length = len(password)
    if length >= 8:
        score += length_weight
        if length >= 12:
            score += length_weight  


    if re.search(r'[A-Z]', password):
        score += upper_weight
    
    
    if re.search(r'[a-z]', password):
        score += lower_weight
    
    
    if re.search(r'\d', password):
        score += digit_weight
    
    
    if re.search(r'[!@#$%^&*(),.?":{}|<>]', password):
        score += special_weight
    
    
    if score >= 7:
        strength = "Very Strong"
    elif score >= 5:
        strength = "Strong"
    elif score >= 3:
        strength = "Moderate"
    else:
        strength = "Weak"
    

    feedback = []
    if length < 8:
        feedback.append("Password is too short. Consider using at least 8 characters.")
    if not re.search(r'[A-Z]', password):
        feedback.append("Add uppercase letters to make your password stronger.")
    if not re.search(r'[a-z]', password):
        feedback.append("Add lowercase letters to make your password stronger.")
    if not re.search(r'\d', password):
        feedback.append("Include numbers to enhance your password security.")
    if not re.search(r'[!@#$%^&*(),.?":{}|<>]', password):
        feedback.append("Include special characters to make your password more secure.")
    
    return {"strength": strength, "score": score, "feedback": feedback}
    
    
    password = "Pass@word2345"
    result = assess_password_strength(password)
    print(f"Password Strength: {result['strength']}")
    print(f"Score: {result['score']}")
    print("Feedback:")
    for message in result['feedback']:
      print(f"- {message}")
