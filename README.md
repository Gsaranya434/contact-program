# contact-program
# import pandas as pd
from core import form

def yaml_file(data):
    Filename='setting.yaml'
    with open(Filename,'w') as file:
        file.write(str(data))

def create_contact(list):
    for x in list:
        choice = input(x + ': ')
        list.update({x:choice})
    yaml_file(list)


def read_contact():
    with open('setting.yaml', 'r') as file:
        print(file.readline())


def update_contact(item):
    print(item)
    yaml_file(item)


def delete_contact():
    new = read_contact.__dict__
    yaml_file(new)
    print(str(new))


def menu1(form):
    print('='*20)
    options = input('enter the number for contact ex:(1.create,2.read,3.update,4,delete,5.back): ')
    if (options== '1'):
        print(form.CRUD[0])
        create_contact(form.list)
    elif (options == '2'):
        print(form.CRUD[1])
        read_contact()
    elif (options == '3'):
        print(form.CRUD[2])
        item0=create_contact(form.list)
        update_contact(item0)
    elif (options == '4'):
        print(form.CRUD[3])
        delete_contact()
    else:
        print(form.CRUD[4])
        print('Nothing to change in this contact')
    return menu1(form)


if __name__=='__main__':
    call=menu1(form)
