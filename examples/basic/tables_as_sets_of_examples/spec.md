
# EU e-VAT country selection

> e-VAT (so called 'Amazon Tax') requires electronic sales to individuals to be taxed according to customer-country VAT rates. But it's often not trivial to decide what the customer country is, because of potentially conflicting information from different sources (IP address, billing, delivery). Furthermore, to avoid potential fines, if some of that information points to countries outside EU, and some points to countries inside EU, we want to collect the tax. 
>
>In cases where different criteria for determining the customer address do not match, we need to decide where to assign the transaction. It's better to err on the side of collecting more tax, than avoiding to collect tax for things that can be challenged later.
>

## If the majority choice is within EU, use it

| IP-address Country |  Billing Country | Delivery Country | Use EU VAT? | Expected EU VAT Country  |
|--------------------|------------------|------------------|-------------|--------------------------|
| GB                 | GB               | GB               | Yes         | GB                       |
| FR                 | GB               | GB               | Yes         | GB                       |
| FR                 | GB               | FR               | Yes         | FR                       |

## If the majority choice is outside EU, but the remaining country is in the EU, use the EU country to be sure

| IP-address Country |  Billing Country | Delivery Country | Use EU VAT? | Expected EU VAT Country  |
|--------------------|------------------|------------------|-------------|--------------------------|
| US                 | US               | FR               | Yes         | FR                       |
| US                 | FR               | US               | Yes         | FR                       |

## If all three countries are different, use the EU country in the priority of Delivery, Billing, IP

| IP-address Country |  Billing Country | Delivery Country | Use EU VAT? | Expected EU VAT Country  |
|--------------------|------------------|------------------|-------------|--------------------------|
| GB                 | DE               | FR               | Yes         | FR                       |
| US                 | RU               | FR               | Yes         | FR                       |
| GB                 | DE               | US               | Yes         | DE                       |
| GB                 | RU               | US               | Yes         | GB                       |

## If all three countries are outside EU, no VAT reporting needed

| IP-address Country |  Billing Country | Delivery Country | Use EU VAT?  |
|--------------------|------------------|------------------|--------------|
| US                 | RU               | NO               | No           |

