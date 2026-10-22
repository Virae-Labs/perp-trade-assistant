# Venue identity and form checks

Read only the sections needed for the supplied legs. UI labels may change: verify current visible controls, not a stored click sequence.

## Hyperliquid

- Official origin: `https://app.hyperliquid.xyz`.
- Navigate using the supplied official URL, then verify the exact `nativeCoin`, including any `dex:` prefix, and that the product is perpetual rather than spot.
- Match the selected trading account to the master address in `ownerAddress`/`externalId`. If a vault or subaccount is selected instead, stop; the current instruction describes the specified master account only.
- Verify that the leverage control belongs to this exact account and `nativeCoin`, including its DEX prefix. Apply only the permitted target leverage and read it back without switching Cross/Isolated mode. Stop for any signing or Enable Trading requirement.
- Read the quantity unit, leverage, margin mode and time-in-force. A limit price attached to a market UI does not prove an IOC limit order. Stop if the exact requested type cannot be represented.
- Let the user complete any Enable Trading/API wallet approval or wallet signing. Do not access an existing agent key or create one.

## Lighter

- Official origin: `https://app.lighter.xyz`.
- The supplied root URL does not identify a market. Use the venue's visible market selector and verify the exact base asset, USDC perpetual product and instrument. `nativeCoin` may be a numeric venue market ID rather than a ticker; compare it where the UI exposes it. If the visible market cannot be matched unambiguously, stop. Match both the L1 owner address and Account Index; owner address alone is insufficient when subaccounts exist.
- Verify Classic/Unified account selection, base quantity units, order type/TIF, leverage and margin mode. If the account index cannot be verified in the UI, stop for user verification rather than filling an unknown account.
- Adjust leverage only for the verified Account Index, Classic/Unified selection and exact perpetual market. Preserve margin mode and read back the target after saving; stop for authorization or signing.
- The browser flow needs no API key entry or key export. Dashboard wallet-only reads may show positions while open orders, receipts and funding history remain unavailable. Never interpret this as proof of no pending orders.

## dYdX

- Official origin: `https://dydx.trade`.
- Match the actual dYdX chain address in `ownerAddress` and the exact `subaccountNumber`; a matching MetaMask or Phantom address alone does not prove the same derived dYdX account. Stop if the selected account cannot be verified.
- Apply leverage only for the verified dYdX address, subaccount and native market. Distinguish the editable market setting from maximum leverage, actual position leverage and total subaccount exposure. Preserve Cross/Isolated mode; stop if changing leverage requires a signature or a collateral transfer.
- Verify the supplied native perpetual market, base quantity, limit price, TIF and observed leverage. Do not confuse a 1x target with proof of a protocol-enforced collateral or loss cap.
- Onboarding signatures can derive a dYdX account key. Never request, read, copy, persist or transmit onboarding signatures, seed phrases, derived keys or permissioned trading keys. Wallet connection/onboarding and signing belong to the user.

## Handoff

Before the user submits, remind them to check the actual account, market, side, units, price, time-in-force, margin/leverage and fees in the official UI. If the instruction expires while preparing the second form, stop and regenerate it; do not silently refresh prices. The user should cancel outstanding orders in these markets before associating snapshots in Dashboard.
