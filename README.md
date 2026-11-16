    contacts = []
    # add
    def add_contact():
        name= input("Enter name:")
        phone= input("Enter phone- number:")
        email = input("Enter email-id")
        if len(phone) !=10 or not phone.isdigit():
            print("Invalid phone number. Enter 10 digit")
            return 
        for c in contacts:
            if c["phone"] == phone:
                print("contact already exist:")
                return
        contact = {"name": name, "phone": phone, "email": email}
        contacts.append(contact)
        print("contact added:",name,"|",phone)

    #view
    def view_contacts():
        if len(contacts) == 0:
            print("No contacts found.")
        for c in contacts:
            print(c["name"],"|",c["phone"],"|",c["email"])

    #Search
    def search_contacts():
        name = input("Enter name to search:")
        found = False
        for c in contacts:
            if name.lower() in c["name"].lower():
                if c["email"] == "":
                    print(c["name"],"|",c["phone"])
                    found = True
        if found == False:
            print("Contact not found.")

    # Update
    def update_contact():
        name = input("Enter name to UpdATE:")
        for c in contacts:
            if c["name"].lower() == name.lower():
                new_phone = input("Enter new phone number: ")
                if len(new_phone) != 10 or not new_phone.isdigit():
                    print("Invalid phone numbee:")
                    return
                for x in contacts:
                    if x["phone"] == new_phone:
                        print("Contact already exist.")
                        return
                c["phone number UPDATED:",  new_phone]
                return
        print("Contact not found.")


    # DELETE
    def delete_contact():
        name = input("Enter name to delete:")
        for c in contacts:
            if c["name"].lower() == name.lower():
                contacts.remove(c)
                print("Contact '" + c["name"] + "' deleted. total contacts:", len(contacts))
                return
        print("Contact not found.")


    while True:
        print()
        print("1. add")
        print("2. view")
        print("3. search")
        print("4.update")
        print("5.delete")
        print("6.exit")
        choice = input("Enter your choice:")

        if choice == "1":
            add_contact()
        elif choice == "2":
            view_contacts()
        elif choice == "3":
            search_contacts()
        elif choice == "4":
            update_contact()
        elif choice == "5":
            delete_contact()
        elif choice == "6":
            print("Bye-Bye")
            break
        else:
            print("Wrong choice")
