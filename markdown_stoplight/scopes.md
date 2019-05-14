#### Scopes

If you want to create an app for a beyondshop you need access to our
merchant's data. By setting OAuth scopes you specify exactly which
permissions your app requires.

Here's the list of the scopes we provide and what they're used for.


| Scope                             | Used for                          |
|-----------------------------------|-----------------------------------|
| `catg:c`                          | Create category                   |
| `catg:r`                          | List categories, Show category details   |
| `catg:u`                          | Update all category properties, Update category partially (json patch), Update category partially (json)   |
| `catg:d`                          | Delete category |
| `clpr:c`                          | Create cancelation processes, Cancel order  |
| `clpr:r`                          | List cancelation processes, Show cancelation process details |
| `cset:r`                          | List checkout settings |
| `cset:u`                          | Update checkout settings |
| `lcnt:u`                          | Update legal content              |
| `legl:r`                          | Show legal details                |
| `legl:u`                          | Update legal resource partially (json patch), Update legal resource partially (json)   |
| `nltg:m`                          | Create newsletter target, Update newsletter target, Delete newsletter target |
| `orde:r`                          | List order events                 |
| `ordn:r`                          | Show order number configuration details   |
| `ordn:u`                          | Update complete order number configuration, Update order number configuration partially      |
| `ordr:r`                          | List orders, Show order details, Show order by cart id           |
| `ordr:u`                          | Update order note, Update billing address, Update shipping address, Create invoice, Send invoice |
| `ordp:r`                          | List order processes              |
| `paym:m`                          | Integrate a payment solution      |
| `prad:c`                          | Create product attribute definition          |
| `prad:r`                          | List product attribute definitions, Show product attribute definition details, Find existing attribute definitions by namespace and name, Find existing attribute definitions by namespace and query |
| `prad:u`                          | Update product attribute definition  |
| `prad:d`                          | Delete product attribute definition  |
| `prat:c`                          | Create product attribute             |
| `prat:r`                          | Retrieve product attribute, Retrieve all product attributes for product   |
| `prat:u`                          | Update product attribute             |
| `prat:d`                          | Delete product attribute               |
| `prda:r`                          | Show product availability details |
| `prda:u`                          | Enable stock management, Disable stock management, Adjust stock level, Update reserve stock, Enable purchasability, Disable purchasability |
| `prod:c`                          | Create product                    |
| `prod:r`                          | List products, Show product details, Find existing attribute values, Find used tags, List product attachments, Show product attachment details, List custom product attributes, List custom product attributes by namespace, List custom product attributes by namespace and attribute name, List product images, Show product image details    |
| `prod:u`                          | Create custom product attribute, Update product partially (json patch), Update product partially (json), Add product attachment, Delete product attachment, Delete custom product attribute, Add product image, Assign product image as default image, Delete product image  |
| `prod:d`                          | Delete product                    |
| `prst:r`                          | Show product settings             |
| `prst:u`                          | Update product settings (json patch)     |
| `pymt:c`                          | Create payment method             |
| `pymt:r`                          | List payment methods, Show payment method details, Generate referral URI  |
| `pymt:u`                          | Update payment method, Sort payment methods, Activate a payment method, Deactivate a payment method       |
| `pymt:d`                          | Delete payment method             |
| `pypr:r`                          | List payment processes, Show payment process details, Show active payment process details    |
| `pypr:u`                          | Mark payment process as voided, Mark payment process as paid  |
| `rfpr:r`                          | List refund processes, Show refund process details, Show active refund process details       |
| `rfpr:u`                          | Mark refund process as paid       |
| `rtpr:c`                          | Create return processes           
| `rtpr:r`                          | List return processes, Show return process details        |
| `scop:r`                          | List all scopes                   |
| `sctg:m`                          | Create script tag, Update script tag, Delete script tag   |
| `shad:r`                          | Show address details              |
| `shad:u`                          | Update address partially (json patch), Update address with tenant context (json)    |
| `shat:c`                          | Create shop attribute             |
| `shat:r`                          | List shop attributes, Show shop attribute details   |
| `shat:u`                          | Update shop attribute             |
| `shat:d`                          | Delete shop attribute             |
| `shcl:c`                          | Open shop, Close shop             |
| `shim:c`                          | Create shop image                 |
| `shim:r`                          | List shop images, Show shop image details, Find shop images by label |
| `shim:d`                          | Delete shop image                 |
| `shop:u`                          | Update shop, Update shop partially (json patch)         |
| `shpr:c`                          | Create shipping processes         |
| `shpr:r`                          | List shipping processes, Show shipping process details       |
| `shpr:u`                          | Mark shipment as shipped, Mark shipment as delivered      |
| `shpz:c`                          | Create shipping zone              |
| `shpz:r`                          | List shipping methods of shipping zone, Show shipping zone details, List shipping zones, Show details of shipping method in shipping zone, Sort shipping methods in shipping zone  |
| `shpz:u`                          | Update shipping zone, Sort shipping zones, Create shipping method in shipping zone, Delete shipping method in shipping zone       |
| `shpz:d`                          | Delete shipping zone              |
| `user:c`                          | Create user, Enable support access        |
| `user:r`                          | List users, Show user details, List user roles, Add user roles, List user searches, Find user by username, Retrieve support access status   |
| `user:u`                          | Set user roles, Add user roles    |
| `user:d`                          | Disable support access            |