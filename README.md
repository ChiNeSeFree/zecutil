# zecutil

Support [Overwinter](https://z.cash/upgrade/overwinter.html) [Sapling](https://z.cash/upgrade/sapling) network upgrade for Zcash. Not support joinsplits.

```go
zecTx := &zecutil.MsgTx{
    MsgTx:        newTx,
}

lookupKey := func(a btcutil.Address) (*btcec.PrivateKey, bool, error) {
    return privKey, wif.CompressPubKey, nil
}
sigScript, err := zecutil.SignTxOutput(
    &params,
    zecTx,
    i,
    prevTxScript,
    txscript.SigHashAll,
    txscript.KeyClosure(lookupKey),
    nil,
    nil,
    amount,
)
if err != nil {
    return err
}

txIn.SignatureScript = sigScript

var buf bytes.Buffer
if err = zecTx.BtcEncode(&buf, 0, wire.BaseEncoding); err != nil {
    return err
}

fmt.Printf("Tx hex: %x\n", buf.Bytes())
fmt.Printf("Tx Hash: %s\n", zecTx.TxHash().String())

```

-------
Forked from [https://github.com/cpacia/bchutil/](https://github.com/cpacia/bchutil/)
