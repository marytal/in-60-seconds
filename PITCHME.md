@snap[north span-100]
![](assets/img/amazon.png)
@snapend

@snap[west span-30]

### The best place on Earth

@snapend

---

@snap[midpoint span-65]

@quote[It's not an experiment if you know it's going to work. - Jeff Bezos]
@snapend

---

@snap[midpoint span-65]

![](assets/img/account.jpg)
@snapend

---

![](assets/img/seller-central.jpg)

---

@snap[north-west]

#### Amazon's Catalog

@snapend

@snap[west span-100]
@ul[spaced]

- UPC
  - US barcode for retail packaging
- EAN
  - European bar code standard
- ISBN
  - International book specific barcode

@ulend

---

### What's an ASIN?

@ul

- A new ASIN is created when an item is added to the Amazon catalog
- When merchants add an existing item (Colgate toothpaste?), the existing ASIN is used
- When merchants add a never-before-listed item, a new ASIN is created for them
- For books, ASIN is the same as ISBN (super fun fact)

@ulend

---

```
# inventory_report_lines

create_table "inventory_report_lines", force: :cascade, options: "ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci" do |t|
  t.integer "shop_id", null: false
  t.integer "offer_id"
  t.string "asin", limit: 25, null: false
  t.string "parent_asin", limit: 25
  t.string "price", limit: 20
  t.string "quantity", limit: 20
  t.string "seller_sku", limit: 40, null: false
  t.datetime "created_at", default: -> { "CURRENT_TIMESTAMP" }, null: false
  t.datetime "updated_at", default: -> { "CURRENT_TIMESTAMP" }, null: false
  t.index ["asin"], name: "index_inventory_report_lines_on_asin"
  t.index ["offer_id"], name: "index_inventory_report_lines_on_offer_id"
  t.index ["parent_asin"], name: "index_inventory_report_lines_on_parent_asin"
  t.index ["shop_id", "parent_asin"], name: "index_inventory_report_lines_on_shop_id_and_parent_asin"
  t.index ["shop_id", "seller_sku"], name: "index_inventory_report_lines_on_shop_id_and_seller_sku", unique: true
  t.index ["updated_at"], name: "index_inventory_report_lines_on_updated_at"
end

```

@[3]
@[6-7]
@[9]
@title[Inventory Report Lines]

---

```
package main

import "fmt"

func main() {
    fmt.Println("Hello, world!")
}
```

@[1]
@[3-8]
@title[Code]

---

## Add Some Slide Candy

![](assets/img/presentation.png)

---

@title[Customize Slide Layout]

@snap[west span-50]

## Customize Slide Content Layout

@snapend

@snap[east span-50]
![](assets/img/presentation.png)
@snapend

---?color=#E58537
@title[Add A Little Imagination]

@snap[north-west]

#### Add a splash of @color[cyan](**color**) and you are ready to start presenting...

@snapend

@snap[west span-55]
@ul[spaced text-white]

- You will be amazed
- What you can achieve
- _With a little imagination..._
- And **GitPitch Markdown**
  @ulend
  @snapend

@snap[east span-45]
@img[shadow](assets/img/conference.png)
@snapend

---?image=assets/img/presenter.jpg

@snap[north span-100 headline]

## Now It's Your Turn

@snapend

@snap[south span-100 text-06]Click here to jump straight into the interactive feature guides in the GitPitch Docs @fa[external-link]](https://gitpitch.com/docs/getting-started/tutorial/)
@snapend
