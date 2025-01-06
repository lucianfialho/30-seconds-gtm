# Convert a String to a Slug

Converts a string into a URL-friendly slug format.

- The snippet removes accents and special characters.
- Replaces spaces and underscores with hyphens (`-`).
- Converts the string to lowercase to ensure consistency.
- Strips out any remaining non-alphanumeric characters.
- Uses ES5-compatible methods to ensure it works in GTM.

```js
function () {
    var input = {{Input Variable}}; // Replace with your GTM variable
    if (typeof input !== "string") return "";

    // Helper function to remove accents
    function removeAccents(str) {
        var accentsMap = {
            'a': /[\xE0-\xE6]/g, 'e': /[\xE8-\xEB]/g, 'i': /[\xEC-\xEF]/g,
            'o': /[\xF2-\xF6]/g, 'u': /[\xF9-\xFC]/g, 'c': /\xE7/g,
            'n': /\xF1/g
        };
        for (var letter in accentsMap) {
            str = str.replace(accentsMap[letter], letter);
        }
        return str;
    }

    // Process the input
    return removeAccents(input)
        .replace(/[^a-zA-Z0-9\s-_]/g, "") // Removes special characters
        .replace(/^\s+|\s+$/g, "") // Trims leading/trailing whitespace
        .replace(/[\s_]+/g, "-") // Replaces spaces/underscores with hyphens
        .toLowerCase(); // Converts to lowercase
}
