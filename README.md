# solo-stakers

This repo is home to Rated’s “solo-staker filter” for the Ethereum Beacon Chain.

In 2023, we set out to answer one of the most persistent unanswered questions in the Ethereum staking ecosystem; “how many solo stakers are there?” We presented our methodology in this [blog post](https://blog.rated.network/blog/solo-stakers), arriving at the finding that ~6.5% of the ETH staked on the Beacon Chain is mapping to solo stakers. 

The filter was further improved in February 2024, after receiving high quality feedback from the Starknet airdrop. The updated filter increased the estimation to 7.2% of the Beacon Chain–as of validator index height 500k.

In this repo we are hosting a suite of materials related with the work, starting with first and foremost with the list of solo-staker mappings. 

*This list has been curated by [Rated](https://rated.network), supported with a grant from [LEGO](https://lego.lido.fi/). Reach out to us on x.com [@ratedw3b](https://twitter.com/ratedw3b), and leave your comments via feedback.rated.network or on the issues section of this repo. You can find us onchain at ratedw3b.eth.*

## Properties of the list

The first version of the list you will find in this repo, considers the **first 500k indices** since genesis (for more info on validator selection please consult the relevant section [here](https://blog.rated.network/blog/solo-stakers)). Over time we plan to refresh the list to account for newer validators, and if there’s demand for it, we might also release the toolchain deployed to produce the list. **Please star this repo to signal interest!**

*Below we outline the variables included in the first release and how to interpret them.*

The [dataset](solo_stakers_v1.csv) contains the following columns:
- `deposit_address`: the address used to initiate the transaction to the deposit contract.
- `confidence`: the aggregate confidence score for that deposit address. 
- `deposit_address_validator_count`: total number of validators under the deposit address in the examined dataset.
- `withdrawal_addresses`: list of withdrawal addresses associated with the validators under the deposit deposit address.
- `avg_activation_epoch`: average activation epoch of validators under this deposit address.
- `related_withdrawal_address_validator_count`: total number of validators under all associated withdrawal addresses in the examined dataset. This is essentially the number of validators all associated withdrawal addresses own.

## Considerations

This is a probabilistic, machine learning based methodology that has helped produce this list. As such it is bound to include false positives and false negatives, although we have gone to great lengths to minimize those. 

Moreover, picking a cutoff value in order bound the set of “high confidence solo addresses” is an exercise in subjectivity. We have traditionally gone with 0.5 as a benchmark, but different use cases might call for different benchmarks.

## Why Open Source the list

There are many valuable use cases we foresee the list serving, including as a filter for entry criteria in curated sets (e.g. Lido CSM, Eigenlayer AVS’s), a filter for airdrops targeting one of the most engaged and competent groups of operators in the industry, and so on.

We’re excited to see how folks innovate with this component.

## License

The dataset is open sourced under [**CC-BY-SA-4.0 license**](LICENSE), which permits sharing and remixing of the open source content assuming proper attribution to Rated and also release of derived works under the same license. Please take the appropriate care to familiarize yourself with the license before using the contents of this repo to build value downstream. 