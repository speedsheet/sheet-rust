# Contributing to Rust SpeedSheet

Thanks for considering a contribution! This speedsheet is community-maintained and we welcome improvements from Rustaceans of all experience levels.

## What We're Looking For

**High-value contributions:**
- Missing Rust features (especially new stable releases)
- Clearer examples for ownership/lifetime patterns
- Real-world use cases and common pitfalls
- Corrections of errors or outdated information
- Additional standard library and ecosystem coverage

**Quick wins:**
- Typo fixes
- Broken links
- Code example improvements
- Better explanations

## Before You Start

1. **Check existing content** - Search the `.stash` file to avoid duplicates
2. **Read the guidelines** - https://speedsheet.io/s/speedsheet_guidelines
3. **Learn Stash format** - https://speedsheet.io/s/stash (simpler than it looks)
4. **Preview locally** - Download the [Stash viewer](https://thinkgo.io/stash) to see your changes rendered

## How to Contribute

### Quick Edits (Typos, Small Fixes)

1. Click the pencil icon on `rust.stash` in GitHub
2. Make your changes
3. Submit a pull request with a clear description

### Larger Contributions (New Sections, Examples)

1. Fork this repo
2. Clone your fork locally
3. Edit `rust.stash` in your preferred editor
4. Test with the Stash viewer (optional but recommended)
5. Commit with descriptive messages: `Add async/await timeout patterns`
6. Push to your fork
7. Submit a pull request

## Stash Format Quick Reference

Lightweight and readable in raw form:
```stash
# Heading Level 1
## Heading Level 2

<cb>code_example()<>

<c>inline_code<>

<b>bold text<>

<*>Bullet point
Another bullet<>
```

**Key elements:**
- `# Heading` - Section headers (use ## for subsections)
- `<cb>code<>` - Code blocks
- `<c>code<>` - Inline code
- `<*>item<>` - Bullet points
- `<#>comment<>` - Comments/notes

Full reference: https://speedsheet.io/s/stash

## Style Guidelines

**Code examples:**
- Keep them short and focused (5-10 lines max)
- Use idiomatic Rust: `user_name` not `x`, prefer `&str` over `String` in signatures
- Show both successful and error cases when relevant
- Include type annotations where they aid clarity
- Compile successfully (preferably tested)
- Add comments for non-obvious lifetime/borrow patterns

**Explanations:**
- Clear and concise - this is a reference, not The Book
- Lead with the most common use case
- Mention ownership/lifetime implications when relevant
- Flag unsafe code clearly
- Use active voice

**Organization:**
- Follow existing section structure
- Add `@` tags for search discoverability
- Cross-reference related sections when helpful
- Note minimum Rust version for newer features

## Example Contribution

**Bad:**
```stash
### option
Some() or None
```

**Good:**
```stash
### Option\\<T>

<cb>enum Option\\<<v>T<>> {
    Some(<v>T<>),
    None,
}<>

Represents an optional value. Either contains a value (<c>Some<>) or doesn't (<c>None<>).

Common patterns:

<cb>let <v>value<> = <v>opt<>.unwrap_or(<v>default<>);
let <v>value<> = <v>opt<>.unwrap_or_else(|| <v>compute_default<>());

if let Some(<v>x<>) = <v>opt<> {
    <#>// use x<>
}<>

Safer than <c>unwrap()<>. Prefer <c>match<>, <c>if let<>, or combinator methods (<c>map<>, <c>and_then<>, etc.) over direct unwrapping.

Example:

<cb>fn find_user(id: u32) -> Option<&'static str> {
    match id {
        1 => Some("Alice"),
        2 => Some("Bob"),
        _ => None,
    }
}

let name = find_user(1).unwrap_or("Guest");
<#>// name = "Alice"<>

let missing = find_user(99).unwrap_or("Guest");
<#>// missing = "Guest"<><>

@
@ Option, Some, None, optional values
```

## Pull Request Guidelines

**Title format:**
- `Add [feature/topic]` - e.g., "Add async trait examples"
- `Fix [issue]` - e.g., "Fix incorrect lifetime annotation in Result section"
- `Update [section]` - e.g., "Update tokio patterns for 1.40 release"

**Description should include:**
- What changed and why
- Rust edition if relevant (2018/2021/2024)
- Link to Rust docs or RFC if applicable
- Screenshot of rendered output (if you have Stash viewer)

## Questions?

- **Format questions:** Check https://speedsheet.io/s/stash
- **Content questions:** Open an issue before large PRs
- **General questions:** Contact me using the [feedback form](https://speedsheet.io/feedback).

## License

By contributing, you agree that your contributions will be licensed under CC BY-NC-SA 4.0, matching the project license. You retain copyright but grant speedsheet.io and others the right to use your contribution under these terms.

See [LICENSE.md](LICENSE.md) for details.

## Recognition

Contributors are appreciated. Significant contributions may be acknowledged in release notes.

---

**Bottom line:** Quality over quantity. A single well-crafted example with proper lifetime annotations beats ten rushed additions. Take your time, and thank you for helping make this speedsheet better!