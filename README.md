# 🧱 4 Pillars of OOP in C# --- Real-World .NET Use Cases (Interview Ready)

This guide explains the four pillars of Object-Oriented Programming
using real production scenarios from enterprise .NET applications.

Designed for: - .NET developers - Angular + .NET full-stack engineers -
Interview preparation (mid--senior level)

------------------------------------------------------------------------

## 📌 What is OOP?

Object-Oriented Programming is a design approach used to build scalable,
maintainable software using objects that contain: - Data (state) -
Behavior (methods)

Four pillars: 1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

------------------------------------------------------------------------

# 1️⃣ Encapsulation --- Protecting Business Data

## Real Production Use Case

Banking / E-commerce order system where total price must not be modified
directly.

``` csharp
public class Order
{
    private decimal _totalAmount;

    public decimal TotalAmount => _totalAmount;

    public void AddItem(decimal price)
    {
        if (price <= 0)
            throw new ArgumentException("Invalid price");

        _totalAmount += price;
    }
}
```

Interview line: Encapsulation protects critical business data and
enforces rules before modification.

------------------------------------------------------------------------

# 2️⃣ Inheritance --- Reusing Common Application Logic

## Real Production Use Case

BaseEntity used across system for audit fields.

``` csharp
public abstract class BaseEntity
{
    public Guid Id { get; set; }
    public DateTime CreatedOn { get; set; }
    public DateTime ModifiedOn { get; set; }
}

public class Product : BaseEntity
{
    public string Name { get; set; }
    public decimal Price { get; set; }
}
```

Interview line: Inheritance centralizes shared logic and avoids
duplication.

------------------------------------------------------------------------

# 3️⃣ Polymorphism --- Same Contract, Different Implementation

## Real Production Use Case

Payment module supporting multiple payment providers.

``` csharp
public interface IPaymentService
{
    Task ProcessPayment(decimal amount);
}

public class UpiPaymentService : IPaymentService
{
    public Task ProcessPayment(decimal amount)
    {
        Console.WriteLine("Processing UPI payment");
        return Task.CompletedTask;
    }
}

public class CardPaymentService : IPaymentService
{
    public Task ProcessPayment(decimal amount)
    {
        Console.WriteLine("Processing card payment");
        return Task.CompletedTask;
    }
}
```

Interview line: Polymorphism enables switching implementations without
changing calling code.

------------------------------------------------------------------------

# 4️⃣ Abstraction --- Hiding System Complexity

## Real Production Use Case

Repository pattern hiding database logic from controllers.

``` csharp
public interface IOrderRepository
{
    Task SaveOrder(Order order);
}

public class SqlOrderRepository : IOrderRepository
{
    public async Task SaveOrder(Order order)
    {
        // SQL DB logic
    }
}
```

Interview line: Abstraction separates what system does from how it does.

------------------------------------------------------------------------

# 🏗 Where OOP Appears in Real .NET Architecture

  Layer                   OOP Pillar Used
  ----------------------- -----------------
  Domain Models           Encapsulation
  Base Entities           Inheritance
  Services via DI         Polymorphism
  Repository Interfaces   Abstraction

------------------------------------------------------------------------

# 🎯 Senior-Level Interview Answer

In real .NET applications: - Encapsulation protects domain data\
- Inheritance centralizes shared behavior\
- Polymorphism enables DI and flexible implementations\
- Abstraction defines architecture boundaries

Used heavily while designing scalable APIs and enterprise systems.
