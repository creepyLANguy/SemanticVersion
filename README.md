# 🏗️ [SemanticVersion - A C# Struct for Versioning](https://github.com/creepyLANguy/SemanticVersion)  

## 📖 Overview  
**SemanticVersion** is a lightweight **C# struct** that provides a robust way to handle **semantic versioning** (`Major.Minor.Patch`).  
It includes:  
✔️ String parsing with error handling  
✔️ Equality and comparison operators (`==, <, >, <=, >=`)  
✔️ Hashing and object equality support  

## 🚀 Features  
- **Easy to Use** → Simple API for version parsing and comparison  
- **Immutable & Efficient** → Struct-based for performance  
- **Correct & Reliable** → Follows semantic versioning best practices  

## 🛠️ Usage  

### ✅ Creating a Semantic Version  
```csharp
var version1 = new SemanticVersion(1, 2, 3);
var version2 = new SemanticVersion("1.2.3");

Console.WriteLine(version1 == version2);  // True
Console.WriteLine(version1 > new SemanticVersion("1.2.2")); // True
```

## 📝 Handling Parsing Errors
```csharp
try 
{
    var invalidVersion = new SemanticVersion("1..2"); // Invalid input
} 
catch (FormatException ex) 
{
    Console.WriteLine($"Error: {ex.Message}");
}
```

## 🧪 Test Cases

| Test Case         | Input String   | Major | Minor | Patch | Expected Behavior |
|------------------|---------------|-------|-------|-------|-------------------|
| **Valid Cases**  |               |       |       |       |                   |
| Standard version | `"1.2.3"`     |   1   |   2   |   3   | ✅ Parses correctly |
| No patch        | `"1.2"`       |   1   |   2   |   0   | ✅ Defaults patch to 0 |
| No minor & patch | `"1"`         |   1   |   0   |   0   | ✅ Defaults minor & patch to 0 |
| Empty string     | `""` (empty)  |   0   |   0   |   0   | ✅ Defaults to `0.0.0` |
| **Negative Values** |           |       |       |       |                   |
| Negative major  | `"-1.2.3"`    |   0   |   2   |   3   | ✅ Converts negative major to 0 |
| Negative minor  | `"1.-2.3"`    |   1   |   0   |   3   | ✅ Converts negative minor to 0 |
| Negative patch  | `"1.2.-3"`    |   1   |   2   |   0   | ✅ Converts negative patch to 0 |
| **Invalid Formats** |           |       |       |       |                   |
| Extra version part | `"1.2.3.4"` |   -   |   -   |   -   | ❌ Should throw FormatException |
| Non-numeric input | `"abc"`      |   -   |   -   |   -   | ❌ Should throw FormatException |
| Mixed valid & invalid | `"1..2"`  |   -   |   -   |   -   | ❌ Should throw FormatException |
| Trailing delimiter | `"1.2."`    |   1   |   2   |   0   | ✅ Treats trailing dot as missing patch |
| Leading delimiter | `".1.2.3"`   |   -   |   -   |   -   | ❌ Should throw FormatException |
| **Edge Cases** |               |       |       |       |                   |
| Single delimiter | `"."`        |   -   |   -   |   -   | ❌ Should throw FormatException |
| Hyphenated version | `"1-2-3"`   |   1   |   2   |   3   | ✅ Parses correctly (hyphens as delimiters) |
| Spaces in version | `" 1.2.3 "`  |   1   |   2   |   3   | ✅ Trims spaces and parses correctly |


## 📜 License

This project is licensed under the MIT License – feel free to use and modify it!

## 🔥 Why This Exists

If you've ever struggled with handling semantic versions in C#, this struct gives you an efficient, reliable, and easy way to parse and compare them.

🚀 Built for speed, accuracy, and maintainability.

## 👀 Next Steps

Want to improve this project? 
Feel free to [submit a PR](https://github.com/creepyLANguy/SemanticVersion/pulls) or [open an issue](https://github.com/creepyLANguy/SemanticVersion/issues)!
