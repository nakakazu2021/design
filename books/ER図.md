::: mermaid
erDiagram
    User {
        varchar userId PK
        varchar department
        varchar name
        varchar email
        varchar password
    }
    Librarian {
        varchar librarianId PK
        varchar department
        varchar name
        varchar email
        varchar password
    }
    Book {
        varchar bookId PK
        varchar category
        varchar title
        varchar author
        varchar publisher
        varchar isbn      
    }
    BookComment {
        varchar bookId PK
        varchar bookCommentId PK
        varchar userId FK
        varchar Comment 
    }
    BookItem {
        varchar bookItemId PK
        varchar bookId FK
        varchar provider
        varchar location 
        varchar status  
    }
    Loan {
        varchar loanId PK
        varchar bookItemId FK
        varchar userId FK
        date checkoutDate
        date returnDate
        date dueDate
        varchar remarks
    }
    Like {
        varchar likeID PK
        varchar bookId FK
        varchar userId FK
    }
    Inventory {
        varchar inventoryId PK
        varchar inventoryYM
        date inventoryDate
        varchar librarianId
    }
    InventoryDetail {
        varchar inventoryId PK
        varchar inventoryDetailId PK
        varchar bookItemId FK
        varchar status
        varchar message
    }
    News {
        varchar newsId PK
        date startDate
        date endDate
        varchar message
    }
    FAQ {

    }

    User ||--|{ Loan : "userId"
    User ||--|{ Like : "userId"
    BookComment }|--|| Book : "bookId"
    User ||--|{ BookComment : "userId"
    Like }|--|| Book : "bookId"
    Book ||--|{ BookItem : "bookId"
    Loan }|--|| BookItem : "bookItemId"
    User ||--|{ BookItem : "provider"
    Librarian ||--o{ Inventory : "librarianId"
    Inventory ||--o{ InventoryDetail : "inventoryId"
    BookItem ||--o{ InventoryDetail : "bookItemId"
:::
