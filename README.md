<h1>"Read Me"</h1>
public Book(String title, String author, String content) {
   <h1>The Gardens of Old</h1> this.title = title;
    this.author = author;
    this.content = content;
}

public String getTitle() {
    return title;
}

public String getAuthor() {
    return author;
}

public String getContent() {
    return content;
}
}

public class ReadMeApp { private ArrayList library;

public ReadMeApp() {
    library = new ArrayList<>();
}

public void addBook(Book book) {
    library.add(book);
}

public void listBooks() {
    System.out.println("Available Books:");
    for (int i = 0; i < library.size(); i++) {
        System.out.println((i + 1) + ". " + library.get(i).getTitle() + " by " + library.get(i).getAuthor());
    }
}

public void readBook(int bookIndex) {
    if (bookIndex <1 || bookIndex > library.size()) {
        System.out.println("Invalid book number.");
        return;
    }
    Book book = library.get(bookIndex - 1);
    System.out.println("\n--- Reading " + book.getTitle() + " by " + book.getAuthor() + " ---");
    System.out.println(book.getContent());
    System.out.println("--- End of " + book.getTitle() + " ---\n");
}

public static void main(String[] args) {
    ReadMeApp app = new ReadMeApp();
    
    app.addBook(new Book("The Great Gatsby", "F. Scott Fitzgerald", "Content of The Great Gatsby..."));
    app.addBook(new Book("1984", "George Orwell", "Content of 1984..."));

    Scanner scanner = new Scanner(System.in);
    while (true) {
        System.out.println("Welcome to the ReadMe App!");
        System.out.println("1. List Books");
        System.out.println("2. Read a Book");
        System.out.println("3. Exit");
        System.out.print("Enter your choice: ");
        
        int choice = scanner.nextInt();
        switch (choice) {
            case 1:
                app.listBooks();
                break;
            case 2:
                System.out.print("Enter the book number to read: ");
                int bookNumber = scanner.nextInt();
                app.readBook(bookNumber);
                break;
            case 3:
                System.out.println("Exiting the app. Goodbye!");
                scanner.close();
                return;
            default:
                System.out.println("Invalid choice, please try again.");
        }
    }
}
