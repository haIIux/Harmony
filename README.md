# Harmony
### ⚠️ This codebase is in active development and is not suited for production use as of yet.

Harmony provides CloudKit sync for GRDB and only GRDB.

## Usage

After installing via Swift Package Manager and enabling CloudKit for your app, add the following to your `App.swift` or equivalent to initialize Harmony. 

```
@Harmony(
    records: [Model1.self, Model2.self],
    configuration: Harmony.Configuration(
            cloudKitContainerIdentifier:  "xxx" \\ Or leave nil for your default container.
            ),
    migrator: // Your GRDB DatabaseMigrator
) var harmony
```

You can then access your Harmony instance from anywhere for writing or reading by simply using:

```
@Harmony var harmony
```

Harmony provides access to write methods that will automatically sync to CloudKit and hides direct database writing access for this purpose. If you write via another means to your GRDB database, Harmony will not see those changes.

Harmony also provides direct access to your `DatabaseReader` if you wish to read directly. I highly suggest seeing if GRDBQuery will fit your needs first. 
