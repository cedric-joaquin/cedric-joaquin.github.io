---
layout: post
title:      "Self Referencing Joins"
date:       2020-10-24 19:27:43 +0000
permalink:  self_referencing_joins
---


For my rails project, I wanted to create a marketplace web-app. The models I needed were:

1. User
2. Auctions
3. Bids

What I wanted to also do was have a user both create and bid on auctions. Essentially, this `User` model needed to have relationships with both the `Auction` and `Bid` models but for different purposes.

First, let's look at our `User` model:
```
class User < ApplicationRecord
    has_many :auctions, foreign_key: :seller_id, class_name: "Auction"
    has_many :bids, foreign_key: :bidder_id, class_name: "Bid"
    has_many :bidded_auctions, through: :bids, source: :auction
end
```
Normally, a standard `has_many` relationship would look like this: `has_many :auctions` However if we look at our `Auction` model setup we notice an issue:
```
class Auction < ApplicationRecord
    belongs_to :seller, foreign_key: :seller_id, class_name: "User"
    has_many :bids
    has_many :bidders, through: :bids
end
```

Our `Auction` model has two references to our `User` depending on its purpose. It has both a `seller` and `bidders`, but they are both from the `User` model. When you call `.seller` on an auction, it won't know what you're talking about because there is no `Seller` model associated to the `Auction` model.

Enter self-referencing joins. We can create different relationships with a single model by defining the foreign key when we create our relationships. For instance, if we want a user to be able to post auctions as a "seller" we would create an association such as:

`has_many :auctions, foreign_key: seller_id, class_name: "Auction"`

The above line of code sets an association with the `Auction` model via: `class_name: "Auction"`. `foreign_key: seller_id` is the name of the foreign key that we add to our `Auction` model in our migrations to create this join table.

We also need to setup our `Auction` model relationships correctly for this to work:

`belongs_to :seller, foreign_key: :seller_id, class_name: "User"`

Again, we set the association with the `User` model, and referencing the foreign key as `seller_id`. But this time, instead of belonging to the `User` model, the auction belongs to a `seller` which is a part of the `User` model. Now when you call `.seller` on an auction, it will reference to a specific `User` that created the auction (aka the seller)

Setting up the bids is exactly the same:

```
class Bid < ApplicationRecord
    belongs_to :bidder, foreign_key: :bidder_id, class_name: "User"
    belongs_to :auction
end

class Auction < ApplicationRecord
    belongs_to :seller, foreign_key: :seller_id, class_name: "User"
    has_many :bids
    has_many :bidders, through: :bids
end

class User < ApplicationRecord
    has_many :auctions, foreign_key: :seller_id, class_name: "Auction"
    has_many :bids, foreign_key: :bidder_id, class_name: "Bid"
    has_many :bidded_auctions, through: :bids, source: :auction
end
```

We create a `bidder` as part of our `User` model the same way we created a `seller` as part of our `User` model for auctions. Now our self-referencing joins table is complete. Our `Auction` references the `User` model with both `sellers` and `bidders`
