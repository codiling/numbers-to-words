# numbers-to-words
def number_to_words(num):
    if num < 0 or num > 999:
        raise ValueError("Input must be between 0 and 999 inclusive.")

    # Define word mappings
    units = ["", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"]
    teens = ["ten", "eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen"]
    tens = ["", "", "twenty", "thirty", "forty", "fifty", "sixty", "seventy", "eighty", "ninety"]
    hundreds = "hundred"

    # Handle special case of zero
    if num == 0:
        return "zero"

    # Convert the number to words
    result = []
    
    # Handle hundreds
    if num >= 100:
        result.append(units[num // 100] + " " + hundreds)
        num %= 100

    # Handle tens and teens
    if num >= 20:
        result.append(tens[num // 10])
        num %= 10
    elif num >= 10:
        result.append(teens[num - 10])
        num = 0

    # Handle units
    if num > 0:
        result.append(units[num])

    return " ".join(result)

# Example usage:
print(number_to_words(123))  # Output: "one hundred twenty three"
print(number_to_words(85))   # Output: "eighty five"
print(number_to_words(0))    # Output: "zero"

