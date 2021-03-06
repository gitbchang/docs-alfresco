---
author: [Alfresco Documentation, Alfresco Documentation]
audience: 
---

# Managing Alfresco keystores

The out-of-the-box Alfresco Content Services installation has a pre-configured main keystore, which contains a secret key generated by Alfresco Content Services. If you want to use encrypted properties, you should create your own keystore with your own password, and update the metadata file appropriately.

The default keystore configuration protects the keys by using two levels of passwords - a keystore password and a password for each key. Currently, the keystore contains only a metadata secret key that is used for encrypting and decrypting node properties that are of type `d:encrypted`.

You can also configure a backup keystore. This is useful in case the keys need to be changed. The user can back up the main keystore to the backup keystore location and create a new keystore in its place.

If both the main and backup keystores are configured, the repository encryption works in the *fallback* mode. In this mode, the node properties are decrypted with the main keystore's metadata key first. If that fails, the backup keystore's metadata key is tried. This allows the keystores to be changed on the disk and reloaded without affecting the running of the repository.

Keystores are used also to protect repository/Solr communications using encryption and mutual authentication. In this case, the keystores store RSA keys and certificates. For more information, see [Solr security](solrsecurity-intro.md).

-   **[Keystore configuration](../concepts/keystore-config.md)**  
You can configure the main and backup keystores using the alfresco-global.properties file.
-   **[Keystore generation](../concepts/keystore-generate.md)**  
Keystore generation can be automatic or manual.
-   **[Keystore key registration](../concepts/keystore-registration.md)**  
The keystore keys are registered with the repository to ensure that they are not accidentally changed.
-   **[Encrypted node properties](../concepts/encrypted-node-properties.md)**  
Data encryption in Alfresco Content Services uses secret keys which are stored in the Java keystore.

**Parent topic:**[Setting up authentication and security](../concepts/auth-intro.md)

