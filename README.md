# MINI-PROJEK-2-KOPER-MAKMUR-HISKYA
HISKYA HARSYAL KILA 2309116089

~~~

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class KoperLinkedList:
    def __init__(self):
        self.head = None
        self.tail = None

    def add_to_front(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node
        if self.tail is None:
            self.tail = new_node

    def add_to_end(self, data):
        new_node = Node(data)
        if self.tail is None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node

    def add_after(self, prev_node, data):
        if not prev_node:
            print("Node sebelumnya tidak ditemukan!")
            return
        new_node = Node(data)
        new_node.next = prev_node.next
        prev_node.next = new_node
        if prev_node == self.tail:
            self.tail = new_node

    def delete_from_front(self):
        if self.head is None:
            print("Linked list kosong!")
            return
        self.head = self.head.next
        if self.head is None:
            self.tail = None

    def delete_from_end(self):
        if self.tail is None:
            print("Linked list kosong!")
            return
        prev_node = self.head
        while prev_node.next != self.tail:
            prev_node = prev_node.next
        prev_node.next = None
        self.tail = prev_node

    def delete_node(self, node):
        if node == self.head:
            self.delete_from_front()
            return
        prev_node = self.head
        while prev_node.next != node:
            prev_node = prev_node.next
        prev_node.next = node.next
        if node == self.tail:
            self.tail = prev_node

    def print_list(self):
        temp = self.head
        while temp:
            print(temp.data, end="==>")
            temp = temp.next
        print()

koper_list = KoperLinkedList()
koper_list.add_to_end("Koper Baller-Hitam")
koper_list.add_to_end("Koper Roaming-Biru")
koper_list.add_to_end("Koper Airwheel-Putih")

while True:
    print("\n========Koper Makmur=======:")
    print("1. Tambah Koper Didepan")
    print("2. Tambah Koper Dibelakang")
    print("3. Tambah Koper Koper Tertentu")
    print("4. Hapus Koper Didepan")
    print("5. Hapus Koper Dibelakang")
    print("6. Hapus Koper Tertentu")
    print("7. Tampilkan Daftar Koper")
    print("8. Keluar")

    choice = input("Masukkan pilihan Anda: ")

    if choice == '1':
        data = input("Masukkan Data Koper(misalnya: Koper Delsey-Silver): ")
        koper_list.add_to_front(data)
        print("Koper Berhasil Ditambahkan ke Depan.")
    elif choice == '2':
        data = input("Masukkan Data Koper(misalnya: Koper Delsey-Silver): ")
        koper_list.add_to_end(data)
        print("Koper Berhasil Ditambahkan ke Belakang.")
    elif choice == '3':
        data = input("Masukkan Data Koper Baru(misalnya: Koper Delsey-Silver): ")
        prev_data = input("Masukkan Data Koper Sebelumnya: ")
        prev_node = koper_list.head
        while prev_node and prev_node.data != prev_data:
            prev_node = prev_node.next
        if prev_node:
            koper_list.add_after(prev_node, data)
            print("Koper Berhasil Ditambahkan Setelah", prev_data)
        else:
            print("Koper Sebelumnya Tidak Ditemukan!")
    elif choice == '4':
        koper_list.delete_from_front()
        print("Koper Depan Berhasil Dihapus.")
    elif choice == '5':
        koper_list.delete_from_end()
        print("Koper Belakang Berhasil Dihapus.")
    elif choice == '6':
        data = input("Masukkan Data Koper yang Ingin Dihapus: ")
        node = koper_list.head
        while node and node.data != data:
            node = node.next
        if node:
            koper_list.delete_node(node)
            print("Koper", data, "Berhasil Dihapus.")
        else:
            print("Koper Tidak Ditemukan!")
    elif choice == '7':
        print("Daftar Koper:")
        koper_list.print_list()
    elif choice == '8':
        print("Program Koper LinkedList Berakhir")
        break
    else:
        print("Pilihan tidak valid. Silahkan masukkan angka antara 1-8.")

~~~
