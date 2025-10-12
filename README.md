# Meteora Dynamic Bonding Curve Trading ( DBC ) Bot

```marmaid
graph TD
    A["Dynamic Bonding Curve<br/>Price Calculation Model"] --> B["Multi-Range Liquidity<br/>Distribution"]
    A --> C["Constant Product<br/>Formula Base"]
    A --> D["Virtual Reserves<br/>Mechanism"]
    
    B --> B1["Price Range 1<br/>pa₁ to pb₁<br/>liquidity = l₁"]
    B --> B2["Price Range 2<br/>pa₂ to pb₂<br/>liquidity = l₂"]
    B --> B3["Price Range N<br/>paN to pbN<br/>liquidity = lN"]
    
    C --> C1["x * y = k<br/>Base Formula"]
    C1 --> C2["x = base_amount<br/>y = quote_amount<br/>k = liquidity²"]
    
    D --> D1["Virtual SOL Reserves"]
    D --> D2["Virtual Token Reserves"]
    D1 --> E["Price Calculation"]
    D2 --> E
    
    E --> E1["Price = virtual_sol_reserves / virtual_token_reserves"]
    E --> E2["Buy: tokens_out = (sol_in * virtual_token_reserves) / (virtual_sol_reserves + sol_in)"]
    E --> E3["Sell: sol_out = (token_in * virtual_sol_reserves) / (virtual_token_reserves + token_in)"]
    
    F["Swap Execution"] --> F1["Find Current Price Range"]
    F1 --> F2["Calculate Amount Using<br/>Range Liquidity"]
    F2 --> F3["Update sqrt_price"]
    F3 --> F4["Move to Next Range<br/>if Needed"]
    F4 --> F5["Sum Total Output"]
    
    G["Key Components"] --> G1["sqrt_start_price<br/>Minimum price in curve"]
    G --> G2["curve: [(sqrt_price, liquidity)]<br/>Up to 20 price ranges"]
    G --> G3["migration_quote_threshold<br/>Graduation trigger"]
    
    H["Formula Details"] --> H1["Δa = L * (1/√P_lower - 1/√P_upper)"]
    H --> H2["Δb = L * (√P_upper - √P_lower)"]
    H --> H3["√P' = √P * L / (L + Δx * √P)"]
    
    style A fill:#e1f5fe
    style E fill:#f3e5f5
    style F fill:#e8f5e8
    style G fill:#fff3e0
    style H fill:#fce4ec
    ```
    
