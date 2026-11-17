# Serenitea Pot Realm Depot Purchase

1. Automates weekly Serenitea Pot Realm Depot purchases on Mondays. Configurable purchases include: Transient Resin, Hero's Wit, Adventurer's Experience, Mystic Enhancement Ore, Mora, Sanctifying Essence, and Sanctifying Unction.
2. Please start the script standing near Tubby (with the dialogue interaction prompt visible).
3. Due to UI form limits hiding entries beyond 7 items, Fabric configuration is omitted and cannot be purchased.
4. Support for purchasing Furnishings, Furnishing Blueprints, Riches of the Realm, Creatures of the Realm (seeds), and Wood may be added in the future.
5. Purchases maximum possible quantity by default; custom purchase quantities are not supported currently.

# Changelog

## 1.1
### Added Day of Week Execution Filter
- The script executes on Mondays by default, but supports customization. For instance, if you want it to run on Tuesdays, Fridays, and Sundays:
  1. Open the script directory and open `main.js` with a text editor.
  2. Replace `ALLOWED_DAYS = [1];` with `ALLOWED_DAYS = [2, 5, 7];`.
  3. Save and close.
