---
author: Alfresco Documentation
---

# Displaying aspect metadata

Add the properties and associations defined on aspects by adding them to the list of fields to show for a type. The aspects that appear can be defined on a type by type basis, and you can control the ordering of the fields.

1.  Open the <web-extension\>\\share-config-custom.xml file.

    **Note:** While you can configure the aspect metadata by directly editing the share-config-custom.xml file in <web-extension\>. It is also possible to deploy custom configurations via JARs or AMPs.

2.  Enter the configuration for custom types.

    The following example configuration shows the `cm:from` and `cm:to` properties for the `cm:effectivity` aspect.

    ```
    
    
    <config evaluator="node-type" condition="cm:content">
       <forms>
          <form>
             <field-visibility>
                <show id="cm:name" />
                <show id="cm:title" force="true" />
                <show id="cm:description" force="true" />
                <show id="mimetype" />
                <show id="cm:author" force="true" />
                <show id="size" for-mode="view" />
                <show id="cm:creator" for-mode="view" />
                <show id="cm:created" for-mode="view" />
                <show id="cm:modifier" for-mode="view" />
                <show id="cm:modified" for-mode="view" />
    
                <!-- cm:effectivity aspect -->
                <show id="cm:from"/>
                <show id="cm:to"/>
             </field-visibility>
          </form>
       </forms>
    </config>
    
    
    ```

3.  Add custom aspects to the default configuration by overriding the configuration.

    The following example shows how to add the fields of an example aspect to all forms for the `cm:content` type.

    ```
    
              
    <config evaluator="node-type" condition="cm:content">
       <forms>
          <form>
             <field-visibility>
                <!-- fields from my example aspect -->
                <show id="my:aspectProperty" />
                <show id="my:aspectAssociation" />
             </field-visibility>
          </form>
       </forms>
    </config>
    
    
    ```

    This will apply the aspects to all `cm:content` nodes.

4.  Save the file.

5.  It is also possible to have the fields appear for any type of node to which the aspect is applied. For example, you may wish to display the `my:aspectProperty` and `my:aspectAssociation` fields for any type of node to which the `my:customAspect` is applied:

    ```
    
              
    <config evaluator="aspect" condition="my:customAspect">
       <forms>
          <form>
             <field-visibility>
                <!-- fields from my example aspect -->
                <show id="my:aspectProperty" />
                <show id="my:aspectAssociation" />
             </field-visibility>
          </form>
       </forms>
    </config>
    
    
    ```


**Parent topic:**[Forms](../concepts/forms-intro.md)

