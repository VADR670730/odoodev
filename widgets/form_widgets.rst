=======
Grafiska element för användning i formulär och trädvyer
=======

Grafiska element för ``many2many`` -fält i Odoo
====

#. ``many2many``  (förvalt)
#. ``many2many_tags`` 
#. ``many2many_checkboxes`` 
#. ``many2many_kanban`` 
#. ``many2many_counter`` 
#. ``many2many_binary`` 


``many2many``  (förvalt)
====

Widgeten ``many2many`` använder en förvald listvy för relaterad modell för att visa en lista av relaterade objekt.

.. image:: many2many_widget.png


**Alternativ**

* ``no_create`` - tar bort "Create" knappen.


**Exempel**

.. code-block:: python

    <field name="field_name" options="{'no_create': True}"/>


Widgeten ``many2many_tags``
****

En Facebookliknande flervalsmarkering.

.. image:: many2many_tags_widget.png

**Alternativ**

* ``no_quick_create`` - tar bort ``Create and edit...`` alternativet.
* ``no_quick_edit`` - tar bort ``Skapa "foo"`` alternativet.
.. image:: many2many_tags_widget2.png
* ``no_create`` - ``no_qick_create`` och ``no_create_edit`` kombinerat.


**Exempel**

.. code-block:: python

    <field name="field_name"
    widget="many2many_tags"
    options="{'no_create_edit': True}"/>


****


Widgeten ``many2many_checkboxes``
****

Enligt en notering i dokumentationen till Odoo::

    This type of field display a list of checkboxes. It works only with m2ms. This field 
    will display one checkbox for each record existing in the model targeted by the 
    relation, according to the given domain if one is specified. Checked records will 
    be added to the relation.


Det finns ingen möjlighet för denna widgt att skapa nya poster, exempelvis produkter.

.. image:: many2many_checkboxes_widget.png


**Exempel**

.. code-block:: python

    <field name="field_name" widget="many2many_checkboxes"/>
    


``many2many_kanban`` widgeten
****

Widgeten ``many2many_kanban`` använder Kanbanvyn för att visa en lista av relaterade objekt.

Denna widget kan varieras på många sätt beroende på vilken Kanbanvy som används. Här är en skärmbild från ``project`` modulen:


.. image:: many2many_kanban_widget.png


**Exempel**

.. code-block:: python

    <field name="field_name" widget="many2many_kanban">
        <kanban>
            <field name="name"/>
            <templates>
                <t t-name="kanban-box">
                    <field name="name"/>
                </t>
            </templates>
        </kanban>
    </field>



``many2many_counter`` widgeten
****

En enkel läs-endast widget som visar en länk med information om antalet relaterade objekt. Länkens målvy kan bli konfigurerad via ``views`` alternativet.

Denna är även användbar med ``one2many`` fält.


.. image:: x2many_counter_widget.png

**Alternativ**

* ``views`` Enligt en kommentar i dokumentationen till Odoos källkod::

    The views to display in the act_window action. Must be a list of tuple whose 
    first element is the id of the view to display (or False to take the default one) 
    and the second element is the type of the view. Defaults to [[false, 
    "tree"], [false, "form"]].

.. code-block:: python

    <field name="field_name" widget="x2many_counter" string="things"/>


``many2many_binary`` widgeten
****

Enligt en notering i dokumentationen till Odoo::

    Widget for (many2many field) to upload one or more file in same time and 
    display in list. The user can delete his files.
    

.. image:: many2many_binary_widget.png

**Exempel**

.. code-block:: python

    <field name="field_name" widget="many2many_binary" string="Attach a file"/>
    
    
    
