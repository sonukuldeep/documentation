---
layout: home
parent: Rust
title: Datatype
---

## Datatypes

1. [Integers](#integer)
- Integers are whole numbers
- They are either signed or unsigned
- Rust defaults to i32 which is the fastest

2. [Floating](#float)
- Numbers with decimals
- f32 and f64 are two tyes
- default is f64

3. [Boolean](#boolean)
- Have a value of either true or false
- specified using keyword bool
- one byte in size

4. [Characters](#character)
- Represent letters
- Specified using char keyword
- Use single quotes
- Four bytes in size

## Integer

An integer is a number without a fractional component. Simply put, the integer data type is used to represent whole numbers.

Integers can be further classified as Signed and Unsigned. Signed integers can store both negative and positive values. Unsigned integers can only store positive values. A detailed description if integer types is given below −
<table>

<tbody><tr>
<th class="ts">Sr.No.</th>
<th class="ts">Size</th>
<th class="ts">Signed</th>
<th class="ts">Unsigned</th>
</tr>
<tr>
<td>1</td>
<td>8 bit</td>
<td>i8</td>
<td>u8</td>
</tr>
<tr>
<td>2</td>
<td>16 bit</td>
<td>i16</td>
<td>u16</td>
</tr>
<tr>
<td>3</td>
<td>32 bit</td>
<td>i32</td>
<td>u32</td>
</tr>
<tr>
<td>4</td>
<td>64 bit</td>
<td>i64</td>
<td>u64</td>
</tr>
<tr>
<td>5</td>
<td>128 bit</td>
<td>i128</td>
<td>u128</td>
</tr>
<tr>
<td>6</td>
<td>Arch</td>
<td>isize</td>
<td>usize</td>
</tr>
</tbody>
</table>

### Integer Range

Each signed variant can store numbers from -(2^(n-1) to 2^(n-1) -1, where n is the number of bits that variant uses. For example, i8 can store numbers from -(2^7) to 2^7 -1 − here we replaced n with 8.

Each unsigned variant can store numbers from 0 to (2^n)-1. For example, u8 can store numbers from 0 to (2^8)-1, which is equal to 0 to 255.

### Integer Overflow

An integer overflow occurs when the value assigned to an integer variable exceeds the Rust defined range for the data type. Let us understand this with an example −
```rs
fn main() {
   let age:u8 = 255;

   // 0 to 255 only allowed for u8
   let weight:u8 = 256;   //overflow value is 0
   let height:u8 = 257;   //overflow value is 1
   let score:u8 = 258;    //overflow value is 2

   println!("age is {} ",age);
   println!("weight is {}",weight);
   println!("height is {}",height);
   println!("score is {}",score);
}
```
The valid range of unsigned u8 variable is 0 to 255. In the above example, the variables are assigned values greater than 255 (upper limit for an integer variable in Rust). On execution, the above code will return a warning − warning − literal out of range for u8 for weight, height and score variables. The overflow values after 255 will start from 0, 1, 2, etc. The final output without warning is as shown below −
```text
age is 255
weight is 0
height is 1
score is 2
```

<hr/> 

## Float

Float data type in Rust can be classified as f32 and f64. The f32 type is a single-precision float, and f64 has double precision. The default type is f64. Consider the following example to understand more about the float data type.
```rs
fn main() {
   let result = 10.00;        //f64 by default
   let interest:f32 = 8.35;
   let cost:f64 = 15000.600;  //double precision
   
   println!("result value is {}",result);
   println!("interest is {}",interest);
   println!("cost is {}",cost);
}
```
The output will be as shown below −
```text
interest is 8.35
cost is 15000.6
```

<hr/> 

### Boolean

Boolean types have two possible values – true or false. Use the bool keyword to declare a boolean variable.
Illustration
```rs
fn main() {
   let isfun:bool = true;
   println!("Is Rust Programming Fun ? {}",isfun);
}
```
The output of the above code will be −
```text
Is Rust Programming Fun ? true
```

<hr/> 

## Character

The character data type in Rust supports numbers, alphabets, Unicode and special characters. Use the char keyword to declare a variable of character data type. Rust’s char type represents a Unicode Scalar Value, which means it can represent a lot more than just ASCII. Unicode Scalar Values range from U+0000 to U+D7FF and U+E000 to U+10FFFF inclusive.

Let us consider an example to understand more about the Character data type.
```rs
fn main() {
   let special_character = '@'; //default
   let alphabet:char = 'A';
   let emoji:char = '😁';
   
   println!("special character is {}",special_character);
   println!("alphabet is {}",alphabet);
   println!("emoji is {}",emoji);
}
```
The output of the above code will be −
```text
special character is @
alphabet is A
emoji is 😁
```