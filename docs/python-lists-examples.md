# 5.2 Παραδείγματα Χρήσης Λιστών με for

## Παράδειγμα 1: Διπλασιασμός Αριθμών
Ας ξεκινήσουμε με ένα απλό παράδειγμα όπου θα διπλασιάσουμε κάθε αριθμό σε μια λίστα. Αυτό το παράδειγμα δείχνει πώς μπορούμε να διατρέξουμε μια λίστα και να δημιουργήσουμε μια νέα με τροποποιημένα στοιχεία.

```python
def double_numbers(numbers):
    """
    Διπλασιάζει κάθε αριθμό στη λίστα.
    
    Args:
        numbers (list): Η αρχική λίστα αριθμών
        
    Returns:
        list: Νέα λίστα με διπλασιασμένους αριθμούς
    """
    doubled = []  # Δημιουργούμε μια κενή λίστα για τα αποτελέσματα
    
    for num in numbers:
        doubled.append(num * 2)
        print(f"Διπλασιασμός του {num} -> {num * 2}")
    
    return doubled

# Παράδειγμα χρήσης
original = [1, 2, 3, 4, 5]
result = double_numbers(original)
print(f"Αρχική λίστα: {original}")
print(f"Νέα λίστα: {result}")
```

## Παράδειγμα 2: Εύρεση Θετικών Αριθμών
Σε αυτό το παράδειγμα θα δούμε πώς μπορούμε να φιλτράρουμε στοιχεία από μια λίστα με βάση μια συνθήκη.

```python
def find_positive_numbers(numbers):
    """
    Βρίσκει όλους τους θετικούς αριθμούς σε μια λίστα.
    
    Args:
        numbers (list): Λίστα με αριθμούς
        
    Returns:
        list: Λίστα με μόνο τους θετικούς αριθμούς
    """
    positive = []
    
    for num in numbers:
        if num > 0:
            positive.append(num)
            print(f"Βρέθηκε θετικός αριθμός: {num}")
    
    return positive

# Παράδειγμα χρήσης
mixed_numbers = [-2, 5, 0, -3, 7, -1, 9]
positive_nums = find_positive_numbers(mixed_numbers)
print(f"Όλοι οι αριθμοί: {mixed_numbers}")
print(f"Θετικοί αριθμοί: {positive_nums}")
```

## Παράδειγμα 3: Υπολογισμός Μέσου Όρου με Δείκτες
Αυτό το παράδειγμα δείχνει πώς μπορούμε να χρησιμοποιήσουμε τη συνάρτηση range() για να προσπελάσουμε στοιχεία με βάση τη θέση τους.

```python
def calculate_running_average(numbers):
    """
    Υπολογίζει τον τρέχοντα μέσο όρο για κάθε θέση της λίστας.
    
    Args:
        numbers (list): Λίστα με αριθμούς
        
    Returns:
        list: Λίστα με τους τρέχοντες μέσους όρους
    """
    averages = []
    
    for i in range(len(numbers)):
        current_sum = sum(numbers[:i+1])
        current_avg = current_sum / (i + 1)
        averages.append(round(current_avg, 2))
        print(f"Θέση {i}: Μέσος όρος μέχρι το {numbers[i]} = {current_avg:.2f}")
    
    return averages

# Παράδειγμα χρήσης
scores = [90, 85, 95, 80, 88]
running_avgs = calculate_running_average(scores)
print(f"Βαθμοί: {scores}")
print(f"Τρέχοντες μέσοι όροι: {running_avgs}")
```

## Παράδειγμα 4: Συνδυασμός Δύο Λιστών
Εδώ θα δούμε πώς μπορούμε να συνδυάσουμε στοιχεία από δύο λίστες χρησιμοποιώντας παράλληλη επανάληψη με zip().

```python
def combine_student_info(names, grades):
    """
    Συνδυάζει ονόματα και βαθμούς μαθητών σε μια λίστα προτάσεων.
    
    Args:
        names (list): Λίστα με ονόματα μαθητών
        grades (list): Λίστα με βαθμούς
        
    Returns:
        list: Λίστα με προτάσεις που συνδυάζουν όνομα και βαθμό
    """
    combined = []
    
    for name, grade in zip(names, grades):
        info = f"Ο/Η {name} πήρε βαθμό {grade}"
        combined.append(info)
        print(info)
    
    return combined

# Παράδειγμα χρήσης
student_names = ["Μαρία", "Γιώργος", "Ελένη"]
student_grades = [95, 87, 92]
student_info = combine_student_info(student_names, student_grades)
print("\nΣυνολικές εγγραφές:")
for info in student_info:
    print(info)
```

## Παράδειγμα 5: Διαχείριση Λίστας Εργασιών
Τέλος, ας δούμε ένα πιο πρακτικό παράδειγμα διαχείρισης μιας λίστας εργασιών.

```python
def manage_tasks(tasks):
    """
    Διαχειρίζεται μια λίστα εργασιών, εμφανίζοντας την κατάσταση κάθε εργασίας.
    
    Args:
        tasks (list): Λίστα με λεξικά που περιέχουν πληροφορίες εργασιών
        
    Returns:
        list: Λίστα με τις ολοκληρωμένες εργασίες
    """
    completed_tasks = []
    
    print("Κατάσταση εργασιών:")
    for i, task in enumerate(tasks, 1):
        status = "Ολοκληρώθηκε" if task["completed"] else "Εκκρεμεί"
        print(f"{i}. {task['title']} - {status}")
        
        if task["completed"]:
            completed_tasks.append(task["title"])
    
    return completed_tasks

# Παράδειγμα χρήσης
todo_list = [
    {"title": "Αγορά τροφίμων", "completed": True},
    {"title": "Πληρωμή λογαριασμών", "completed": False},
    {"title": "Άσκηση", "completed": True},
    {"title": "Διάβασμα", "completed": False}
]

completed = manage_tasks(todo_list)
print(f"\nΟλοκληρωμένες εργασίες: {completed}")
```

Κάθε παράδειγμα επιδεικνύει διαφορετικές πτυχές της χρήσης των λιστών με επαναλήψεις for:

1. Το πρώτο παράδειγμα δείχνει τη βασική επεξεργασία στοιχείων
2. Το δεύτερο παράδειγμα δείχνει το φιλτράρισμα στοιχείων
3. Το τρίτο παράδειγμα δείχνει τη χρήση δεικτών και αθροιστικούς υπολογισμούς
4. Το τέταρτο παράδειγμα δείχνει το συνδυασμό στοιχείων από διαφορετικές λίστες
5. Το πέμπτο παράδειγμα δείχνει τη διαχείριση πιο σύνθετων δομών δεδομένων

Κάθε παράδειγμα περιλαμβάνει:
- Σαφή περιγραφή του σκοπού
- Αναλυτικά σχόλια στον κώδικα
- Παραδείγματα χρήσης
- Εκτύπωση ενδιάμεσων αποτελεσμάτων για καλύτερη κατανόηση
