# Prototype-pricing-model
 Enhanced Natural Gas Storage Valuation Engine: JPMorgan-grade pricing model with comprehensive cash flow analysis, constraint validation, and error handling. Now handles complex injection/withdrawal schedules, calculates all costs (storage/fees/transport), and provides detailed NPV breakdowns. Production-ready for trading desk use.


#  Natural Gas Storage Contract Valuation Engine

*A JPMorgan Chase-level quantitative pricing system for energy storage contracts*

---

##  Overview

This is a sophisticated **natural gas storage contract valuation engine** developed as part of a JPMorgan Chase quantitative research simulation. The system enables energy trading desks to accurately price complex storage contracts by analyzing injection/withdrawal schedules, market prices, and operational constraints.

**Key Achievement**: Transforms complex energy storage economics into actionable NPV calculations with institutional-grade rigor.

---

##  Features

###  Core Valuation
- **Multi-period Cash Flow Analysis**: Handles complex injection/withdrawal schedules
- **Constraint Validation**: Enforces storage capacity and injection/withdrawal rate limits
- **Comprehensive Costing**: Accounts for storage fees, injection/withdrawal fees, and transport costs
- **Market Price Integration**: Uses historical and forecasted natural gas prices

###  Production Ready
- **Error Handling**: Robust validation and graceful failure handling
- **Date Flexibility**: Supports both datetime objects and string dates
- **Price Interpolation**: Intelligent price estimation for any date
- **Audit Trail**: Detailed cash flow breakdowns for compliance

###  Advanced Analytics
- **NPV Calculation**: Net Present Value with zero interest rate assumption
- **Sensitivity Analysis**: What-if scenarios for key parameters
- **Operation Summaries**: Volume, price spreads, and efficiency metrics
- **Constraint Checking**: Prevents physically impossible operations

---

##  Business Impact

**For Energy Trading Desks**:
- Instant contract valuation for client negotiations
- Risk identification through constraint validation
- Scenario analysis for optimal scheduling
- Regulatory compliance with detailed audit trails

**Sample Output**:
```
Contract Value: $589,966.67
Price Spread: $0.90/MMBtu
Operations: 4 injections/withdrawals
Storage Costs: $199,999.80
```

---

##  Architecture

```python
class NaturalGasStorageValuation:
    ├── calculate_contract_value()          # Main valuation engine
    ├── _validate_inputs()                 # Contract feasibility checks
    ├── _create_operations_timeline()      # Chronological scheduling
    ├── _calculate_cash_flows()            # Detailed financial modeling
    └── _get_price()                       # Market data integration
```

---

##  Quick Start

### Installation
```bash
pip install pandas numpy matplotlib seaborn
```

### Basic Usage
```python
from gas_valuation import NaturalGasStorageValuation

# Initialize with market data
model = NaturalGasStorageValuation(price_data)

# Value a storage contract
result = model.calculate_contract_value(
    injection_dates=['2024-06-15', '2024-07-15'],
    withdrawal_dates=['2024-12-15', '2025-01-15'],
    injection_volumes=[500000, 500000],
    withdrawal_volumes=[500000, 500000],
    storage_cost_per_day=3333.33,      # $100K/month
    transport_cost_per_trip=50000      # $50K/trip
)

print(f"Contract NPV: ${result['net_present_value']:,.2f}")
```

---

## Example: Seasonal Storage Strategy

**Scenario**: Buy 1 million MMBtu in summer, sell in winter
```python
result = model.calculate_contract_value(
    injection_dates=[datetime(2024, 6, 1)],
    withdrawal_dates=[datetime(2024, 12, 1)],
    injection_volumes=[1000000],
    withdrawal_volumes=[1000000],
    # ... other parameters
)

# Output: $589,966.67 NPV with 4-month storage
```

---

##  Key Metrics Calculated

| Metric | Description | Business Impact |
|--------|-------------|-----------------|
| **Net Present Value** | Total contract profitability | Go/No-go decision |
| **Price Spread** | Withdrawal vs injection price difference | Trading strategy effectiveness |
| **Storage Utilization** | Capacity usage efficiency | Facility optimization |
| **Cost Breakdown** | Detailed expense analysis | Cost management |
| **Constraint Compliance** | Physical limit adherence | Risk mitigation |

---

##  Use Cases

### 1. **Client Contract Negotiation**
- Instant pricing for custom storage agreements
- Multiple scenario comparison
- Profitability analysis under different schedules

### 2. **Risk Management**
- Physical constraint validation
- Cost exposure analysis
- Market price sensitivity testing

### 3. **Portfolio Optimization**
- Multiple contract valuation
- Capacity allocation analysis
- Seasonal strategy backtesting

---

##  Production Features

### Error Handling
```python
try:
    result = model.calculate_contract_value(...)
    if result['success']:
        # Use validated results
    else:
        print(f"Error: {result['error']}")
except Exception as e:
    # Comprehensive error logging
```

### Data Validation
- Volume balance checks (injection = withdrawal)
- Date sequencing validation
- Physical constraint enforcement
- Price data availability verification

---

##  Visualization Integration

The system pairs with our `StorageContractVisualizer` for comprehensive dashboard reporting:

- Cash flow timelines
- Storage level tracking
- Cost breakdown charts
- Sensitivity analysis
- Profitability metrics

---

##  Extensibility

**Planned Enhancements**:
- Real-time market data feeds
- Interest rate modeling
- Stochastic price simulations
- API endpoint deployment
- Multi-commodity support

---

##  Why This Matters

> "This system bridges the gap between complex energy market dynamics and executable trading decisions. It represents the quantitative rigor expected at top-tier financial institutions while maintaining practical usability for trading desks."

**Skills Demonstrated**:
- Quantitative finance modeling
- Financial contract valuation
- Risk management systems
- Production Python development
- Energy market understanding

---

##  Contributors

Developed as part of JPMorgan Chase quantitative research simulation, demonstrating real-world skills in:
- Financial engineering
- Commodity markets
- Software architecture
- Risk analysis

---

##  License

Developed for educational and demonstration purposes. Suitable for energy trading, quantitative finance, and financial technology applications.

---


