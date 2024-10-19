import pickle
import json

def write_contacts_to_file_pickle(filename, contacts):
    with open(filename, 'wb') as file:
        pickle.dump(contacts, file)

def read_contacts_from_file_pickle(filename):
    with open(filename, 'rb') as file:
        return pickle.load(file)

def write_contacts_to_file_json(filename, contacts):
    data = {"contacts": contacts}
    with open(filename, 'w') as file:
        json.dump(data, file, indent=4)

def read_contacts_from_file_json(filename):
    with open(filename, 'r') as file:
        data = json.load(file)
        return data.get("contacts", [])

contacts = [
    {
        "name": "Allen Raymond",
        "email": "nulla.ante@vestibul.co.uk",
        "phone": "(992) 914-3792",
        "favorite": False
    },
    {
        "name": "Logan Paul",
        "email": 'Logan28@gmail.com',
        "phone": "(380) 96-635-0518",
        "favorite": True
    }
]

write_contacts_to_file_pickle('contacts.pickle', contacts)
loaded_contacts_pickle = read_contacts_from_file_pickle('contacts.pickle')
print("Contacts loaded using pickle:")
print(loaded_contacts_pickle)

write_contacts_to_file_json('contacts.json', contacts)
loaded_contacts_json = read_contacts_from_file_json('contacts.json')
print("\nContacts loaded using json:")
print(loaded_contacts_json)
