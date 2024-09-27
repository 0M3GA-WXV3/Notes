def q1(radius):
    # Given the radius of a sphere, calculate and return 
    # its surface area. Surface area is given by the following:
    # A = 4*PI*(r**2) where PI is the constant 3.14159 and r
    # is the radius of the sphere
    
    A = 4*3.14159*(radius**2)
    return A
    pass

def q2(addr):
    # Given an IPv4 address as a string in dotted decimal notation,
    # return True if the address is multicast, otherwise return False.
    # IPv4 multicast addresses are those in the range 224.0.0.0 to
    # 239.255.255.255.
    # ipaddress.IPv4Address has been disabled for this function.
    

    parts = addr.split('.')
    if len(parts) != 4:
        return False    if len(parts) != 4:
 23         return False
 24 
 25     try:
 26         octets = [int(part) for part in parts]
 27 
 28     if 224 <= octets[0] <= 239:
 29         return True
 30      else:
 31         return False
 32     except ValueError:
 33         return False


    try:
        octets = [int(part) for part in parts]

        if 224 <= octets[0] <= 239:
            return True
        else:
            return False
    except ValueError:
        return False    if len(parts) != 4:
 23         return False
 24 
 25     try:
 26         octets = [int(part) for part in parts]
 27 
 28     if 224 <= octets[0] <= 239:
 29         return True
 30      else:
 31         return False
 32     except ValueError:
 33         return False

    pass

def q3():
    # Return the well-known ports as a list of integers.
    # Ports 0 through 1023 are considered well-known.
    lst = range(0, 1024) 
    a = list(lst) 
    return a
    pass

def q4(number):
    # Given a string for a number spelled out as a word,
    # return the number as an integer. The number will
    # only be 'zero','one','two','three', or 'four'
    if number == 'zero':
        return 0
    elif number == 'one':
        return 1
    elif number == 'two':
        return 2
    elif number == 'three':
        return 3
    elif number == 'four':
        return 4    
    pass

def q5():
    middle_initial = middle[0] if middle else ""
    email = f"{first.lower()}.{middle_initial.lower()}.{last.lower()}@{domain.lower()}.com"
    print(email)
    # Read a string from the user and return the integer conversion of it.
    # Ensure the conversion is successful by removing any non-numeric characters.
    # You may assume that the input will contain at least 1 numeric character.

    user_input = input("Enter a string containing at least one numeric character: ")
    numeric_chars = [char for char in user_input if char.isdigit()]
    numeric_string = ''.join(numeric_chars)
    result = int(numeric_string)
    return result
    pass

def q6(first,middle,last,domain):
    # Given a name and domain, print to the screen their email address.
    # The address should take the form: 
    # <first>.<middle initial>.<last>@<domain>.com
    # Only include a middle initial (the first letter of the middle name).
    # Ensure the address is all lowercase.
    # Append '.com' to the given domain
   
    
    
    middle_initial = middle[0] if middle else ""
    email = f"{first.lower()}.{middle_initial.lower()}.{last.lower()}@{domain.lower()}.com"
    print(email)
    pass
def q7(infile,outfile):
    # Copy the contents of the file whose filename is given in 
    # infile to the file whose name is given in outfile. Overwrite
    # outfile if it already exists.
    # shutil.copyfile, copy, and copy2 have been disabled for this function.
    with open(infile, 'r') as in_file:
        contents = in_file.read()
        with open(outfile, 'w') as out_file:
            out_file.write(contents)
    pass

def q8(address):
    # Given an email address of the form:
    # <first>.<middle initial>.<last>@<domain>.com
    # return the 4 elements of the address as a tuple in the order
    # that they appear in the address.
    # For example, if given 'nicholas.r.yost@somedomain.com,
    # ('nicholas','r','yost','somedomain') should be returned.
    
    local_part, domain = address.split('@')
    first, middle, last = local_part.split('.')
    domain = domain.split('.')[0]
    return (first, middle, last, domain)
    pass
def q9(strng):
    # Given a string, return a dictionary whose keys are the set of
    # unique characters within the string and whose values are the
    # count of occurances of each character.
    # For example, if given 'hello', the returned dictionary should be
    # { 'l':2, 'h':1, 'e':1, 'o':1 }
    # collections.Counter has been disabled for this function.
    char_count = {}
    for char in strng:
        if char in char_count:
            char_count[char] += 1
        else:
            char_count[char] = 1

    return char_count
    pass
def q10():
    # Return your last name as a string. Use all lowercase letters.
    return 'garver'
    pass

if __name__ == '__main__':
    
 pass

# PRINTS MY NAME IN ALL CAPS 
def get_uppercase_name():
    return "KYLE"

# Call the function and print the result
print(get_uppercase_name())

def calculate_cuboid_volume(length, width, height):
    return length * width * height

# Example usage:
length = 5
width = 3  # declares variables the declares a volume variable that uses the cuboid vol function where it launches the bodie mathing 
height = 2
volume = calculate_cuboid_volume(length, width, height)
print(f"The volume of the cuboid is: {volume}")


def q6(f0, f1)
diffs = [] 
linenumber = 0
with open(f0) as file0:
  with open(f1) as file1:
    for l0,l1 in zip(file0,file1):
      if l0 != l1:
        diffs.append(linenumber)
      linenumber+=1
retuen diffs
