## Project Cost Summary

| Category | Approx Total |
|----------|-------------|
| Compute (VM, auto-shutdown + deallocation) | ~$8 |
| Sentinel ingestion (within free trial) | ~$0 |
| Logic Apps (few runs) | <$1 |
| Identity (P2/E5 trials — cancelled before billing) | $0 |
| **Total project cost** | **~$10** |

## Cost Management Lessons
- Auto-shutdown on all VMs prevented idle billing
- Deallocated (not just shut down) VMs when not in use compute billing stops
- Used free trials (E5, Sentinel, Entra P2) with tracked cancellation dates
- Requested VM quota increases rather than paying for oversized SKUs
- Kept Defender for Cloud on the free Foundational tier (paid plans off)
