## 🐍 C# Mini-Project: Pokémon Trainer Simulator

### 🎯 Goal

Build a simple Pokémon simulation in C#. The project will help you demonstrate:

- Encapsulation (fields + validation)
- Inheritance and abstraction
- Polymorphism
- Interface implementation
- Using enums and working with composition

---

### 📚 Background

You're creating a mini battle simulator for a Pokémon training program. Each Pokémon has an element type, can attack, and some can evolve. Your trainer can level up their Pokémon and observe their attacks.

---

### 📅 Instructions

#### 1. Define the `ElementType` Enum

Create an `enum` called `ElementType` with the values:

- `Fire`
- `Water`
- `Electric`

This will be used for both Pokémon and attacks.

---

#### 2. Create the `Attack` Class

Define a class `Attack` with:

- `string Name`
- `ElementType Type`
- `int BasePower`

Include a method:

```csharp
public void Use(int level)
```

It should write out a message to the console like this:

```
Flamethrower hits with total power 22!
```

Where 22 is `BasePower + level`.

---

#### 3. Create Predefined Attacks

Before the program starts (e.g. in `Main()`), create at least **2 attacks for each type** and assign them to variables:

```csharp
var flamethrower = new Attack("Flamethrower", ElementType.Fire, 12);
var ember = new Attack("Ember", ElementType.Fire, 6);
```

You will later assign these to Pokémon.

---

#### 4. Create an abstract class Pokemon with the following:

Use public properties and apply validation logic to ensure data integrity.

- A public property for `Name` (2–15 characters)

- A public property for `Level` (must be ≥ 1)

- A property for `Type` representing the Pokémon's elemental type

- A `List<Attack>` field called `Attacks`, which should be passed in and set via the constructor. This list will represent the attacks that a Pokémon knows

- Three methods:

```csharp
public void RandomAttack(){
  // Picks a random attack from the list of attacks and invokes its .Use-method.
};

public void Attack(){
  // Lets the user pick an attack from the list of attacks and invoke its .Use-method.
}:

public void RaiseLevel(){
  // That should increment the level of the given pokemon and print that the pokemon has leveled up.
};
```

---

#### 5. Create 3 Pokémon Subclasses

Create three generic subclasses for each type:

- `FirePokemon : Pokemon`
- `WaterPokemon : Pokemon`
- `ElectricPokemon : Pokemon`

These should automatically set the `Type` field to the corresponding enum value (`ElementType.Fire`, `ElementType.Water`, or `ElementType.Electric`).

Then, create at least 3 named Pokémon subclasses (e.g. `Charmander`, `Squirtle`, `Pikachu`) that inherit from the appropriate type-specific class:

- `Charmander : FirePokemon`
- `Squirtle : WaterPokemon`
- `Pikachu : ElectricPokemon`

---

#### 6. Add an Evolvable Interface

Create an interface:

```csharp
public interface IEvolvable
{
    void Evolve();
}
```

Let at least one Pokémon implement this interface. When evolved, it should:

- Change its `Name`
- Increase its `Level` by 10
- Print a message like:

```
Pikachu is evolving... Now it's Raichu! Level 25!
```

---

#### 7. Simulate the Trainer

In your `Main()` method:

- Create several Pokémon and store them in a `List<Pokemon>`
- Call `RaiseLevel()` and `Attack()` on each
- If a Pokémon is `IEvolvable`, call its `Evolve()` method

---

### ✅ Example Output

```
Charmander leveled up to 6!
Flamethrower hits with total power 18!
Pikachu leveled up to 15!
Thunderbolt hits with total power 25!
Pikachu is evolving... Now it's Raichu! Level 25!
```

---

### ❓ Reflection Questions

Answer the following questions based on the code you’ve written and tested:

1. **F:** When you create a Pokémon and try to access its fields directly – does it work? Why or why not?
2. **F:** If you later want to add a new property that applies to all **Electric-type Pokémon**, where should you place it to avoid repetition?
3. **F:** If instead the new property should apply to **all Pokémon**, where would be the correct place to define it?
4. **F:** What happens if you try to add a `Charmander` to a list that only allows `WaterPokemon`?
5. **F:** You want to store different types of Pokémon – `Charmander`, `Squirtle`, and `Pikachu` – in the same list. What type should the list have for that to work?
6. **F:** When you loop through the list and call `Attack()`, what ensures that the correct attack behavior is executed for each Pokémon?
7. **F:** If you create a method that only exists on `Pikachu`, why can’t you call it directly when it’s stored in a `List<Pokemon>`? How could you still access it?

---

### 💼 Deliverables

- All code should be well-structured in separate files if possible.
- Avoid hardcoding values in methods (pass level to attack, for example).
- You may add more Pokémon, attacks, or features as bonus.

Good luck, Trainer! 🌟
