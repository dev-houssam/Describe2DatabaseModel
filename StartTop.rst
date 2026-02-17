#![allow(unused)]
fn main() {

    // **Unit-like** structs have no fields and are useful for implementing a
    // trait on a type without storing any data in the type itself.
    struct UnitLike;

    struct Color(u8, u8, u8);
    let black = Color(0, 0, 0);

    // Defining a **Named-Field** struct, with fields and methods. The naming
    // convention for structs is 'CamelCase'.
    struct Code {
        source: string,
        destination: string,
    }
    impl Code {

        fn new(width: u32, height: u32) -> Rectangle {
            Rectangle { width, height }
        }

        fn area(self) -> u32 {
            self.width * self.height
        }

        fn can_hold(&self, other: &Rectangle) -> bool {
            self.width > other.width 
                && self.height > other.height
        }


        fn increase_size(&mut self, width: u32, height: u32) {
            self.width += width;
            self.height += height;
        }

        // We can also return 'Self' from a method, which is useful for chaining
        // method calls.
        fn set_width(mut self, width: u32) -> Self {
            self.width = width;
            self
        }
    }

    // Creating an instance of the 'Rectangle' struct
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    // Creating an instance of the Rectangle struct using the associated
    // function 'new'.
    let rect2 = Rectangle::new(30, 50);

    // Create a struct by using struct update syntax to use the fields of another
    // instance of the same struct.
    let rect3 = Rectangle { width: 30, ..rect1 };
    pub struct Person {
        pub name: String,
        age: u8,
    }

    impl Rectangle {
        fn print(&self) {
            println!(
                "Rectangle: {} x {}", self.width, self.height,
            );
        }
    }

    // We can set default values for struct fields using the 'Default' trait.
    #[derive(Default)]
    struct Point {
        x: i32,
        y: i32,
    }

    // We can instantiate a struct with default values using the 'Default' trait.
    let point = Point::default();

    // We can also override some of the default values, when instantiating the
    // struct.
    let other_point = Point {
        x: 10,
        ..Point::default()
    };

    impl Default for Rectangle {
        fn default() -> Rectangle {
            Rectangle {
                width: 10,
                height: 10,
            }
        }
    }
}
