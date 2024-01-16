# polkadot-ecosystem
https://github.com/polkadot-evm/frontier.git
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MetadataToken is ERC20, ERC20Burnable, Ownable {
    string private _tokenURI;

    constructor(
        string memory name,
        string memory symbol,
        string memory tokenURI
    ) ERC20(name, symbol) {
        _tokenURI = tokenURI;
    }

    function setTokenURI(string memory newTokenURI) external onlyOwner {
        _tokenURI = newTokenURI;
    }

    function tokenURI() public view returns (string memory) {
        return _tokenURI;
    }
}
