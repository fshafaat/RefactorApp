# Payment Processing System - Code Refactoring Exercise

## Overview

This repository contains a simple console application that simulates a basic payment processing system. The application, as provided, has several design flaws that violate the SOLID principles of object-oriented programming. Your task is to refactor the code to improve its design, making it more maintainable, extensible, and compliant with the SOLID principles.

## Problem Statement

The current implementation of the payment processing system is tightly coupled, difficult to extend, and violates several SOLID principles:

1. **Single Responsibility Principle (SRP)**: The `PaymentProcessor` class is responsible for handling multiple types of payments, leading to a lack of cohesion.
2. **Open/Closed Principle (OCP)**: The `PaymentProcessor` class is not open for extension. Adding new payment methods would require modifying the existing code, which is against the OCP.
3. **Liskov Substitution Principle (LSP)**: Although not directly violated, the code could benefit from a design that better supports abstraction.
4. **Interface Segregation Principle (ISP)**: The code does not currently use interfaces, and there is a lack of clear segregation of responsibilities.
5. **Dependency Inversion Principle (DIP)**: The code is tightly coupled with specific payment processing implementations, without using dependency injection.

## Your Task

1. **Refactor the Code**: Refactor the existing code to adhere to the SOLID principles. 
   - Introduce interfaces or abstract classes where appropriate.
   - Ensure that the `PaymentProcessor` class is decoupled from specific payment methods.
   - Implement dependency injection to allow for flexible and extensible code.
   
2. **Maintain Functionality**: The refactored code should maintain the same functionality as the original implementation.

3. **Demonstrate Your Changes**: Update the `Main` method in the `Program` class to demonstrate that your refactored code works as expected.

## Original Code

```csharp
using System;

namespace PaymentProcessing
{
    public class PaymentProcessor
    {
        public void ProcessCreditCardPayment(string cardNumber, decimal amount)
        {
            Console.WriteLine($"Processing credit card payment: {amount} using card: {cardNumber}");
            // Imagine this is where the payment is processed.
        }

        public void ProcessPayPalPayment(string email, decimal amount)
        {
            Console.WriteLine($"Processing PayPal payment: {amount} using email: {email}");
            // Imagine this is where the payment is processed.
        }

        public void ProcessPayment(string paymentType, string paymentDetails, decimal amount)
        {
            if (paymentType == "CreditCard")
            {
                ProcessCreditCardPayment(paymentDetails, amount);
            }
            else if (paymentType == "PayPal")
            {
                ProcessPayPalPayment(paymentDetails, amount);
            }
            else
            {
                throw new Exception("Invalid payment type");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            PaymentProcessor processor = new PaymentProcessor();
            processor.ProcessPayment("CreditCard", "1234-5678-9012-3456", 100.0m);
            processor.ProcessPayment("PayPal", "user@example.com", 50.0m);
        }
    }
}
```

## Expected Outcome

By the end of this exercise, you should have a codebase that adheres to the SOLID principles, with a `PaymentProcessor` class that is flexible, easy to extend, and decoupled from the specific payment methods.

## Submission

Please fork this repository, refactor the code as per the instructions, and submit a pull request with your changes. Include a brief explanation of the changes you made and why they improve the code quality.

---

