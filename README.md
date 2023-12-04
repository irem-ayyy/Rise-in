# Rise-in

Aşama 1 - update_portfolio Fonksiyonunu Oluşturun:

rust
Copy code
public entry fun update_portfolio(devhub: &mut DevHub, id: u64, new_portfolio: String, ctx: &mut TxContext) {
    let user_card = object_table::borrow_mut(&mut devhub.cards, id);
    assert!(tx_context::sender(ctx) == user_card.owner, NOT_THE_OWNER);

    user_card.portfolio = new_portfolio;

    event::emit(
        PortfolioUpdated {
            name: user_card.name,
            owner: user_card.owner,
            new_portfolio: new_portfolio,
        }
    );
}
Aşama 2 - PortfolioUpdated Etkinliğini Oluşturun;

struct PortfolioUpdated has copy, drop {
    name: String,
    owner: address,
    new_portfolio: String,
}
Bonus Aşama - update_portfolio Fonksiyonunu Güncelleyin:


public entry fun update_portfolio(devhub: &mut DevHub, id: u64, new_portfolio: String, ctx: &mut TxContext) {
    let user_card = object_table::borrow_mut(&mut devhub.cards, id);
    assert!(tx_context::sender(ctx) == user_card.owner, NOT_THE_OWNER);

    user_card.portfolio = new_portfolio;

    event::emit(
        PortfolioUpdated {
            name: user_card.name,
            owner: user_card.owner,
            new_portfolio: new_portfolio,
        }
    );
}
Bu kodları Rust dilinde bir proje içinde kullanmanız gerekecektir. Eğer bu konuda deneyiminiz yoksa, Rust'un resmi belgelerine göz atabilir veya ihtiyacınız olursa daha fazla yardım almak için bana sorular yönlendirebilirsiniz.
