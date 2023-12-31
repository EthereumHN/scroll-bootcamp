# Scroll Bootcamp

## Recursos Bootcamp
- Ambiente de desarrollo online: https://remix.ethereum.org/
- Descripción del lenguage: https://docs.soliditylang.org/en/v0.8.23/layout-of-source-files.html
- Slides Scroll: https://docs.google.com/presentation/d/1QTQi0iTter5slpKo0iriAG8Sjq0A7pLBGzKSryah1-8/edit?usp=sharing
- Repositorio Frontend: https://github.com/jdestephen/web3-frontend-basics

## Código

### Hola Mundo

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;
contract MyContract {
    function helloWorld() public pure returns (string memory) {
        return "Hello, World!";
    }
}
```

### Almacenamiento
```solidity
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.4.16 <0.9.0;

contract SimpleStorage {
    uint storedData;

    function set(uint x) public {
        storedData = x;
    }

    function get() public view returns (uint) {
        return storedData;
    }
}
```

### Moneda

```solidity
// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.4;

contract Coin {
    // The keyword "public" makes variables
    // accessible from other contracts
    address public minter;
    mapping(address => uint) public balances;

    // Events allow clients to react to specific
    // contract changes you declare
    event Sent(address from, address to, uint amount);

    // Constructor code is only run when the contract
    // is created
    constructor() {
        minter = msg.sender;
    }

    // Sends an amount of newly created coins to an address
    // Can only be called by the contract creator
    function mint(address receiver, uint amount) public {
        require(msg.sender == minter);
        balances[receiver] += amount;
    }

    // Errors allow you to provide information about
    // why an operation failed. They are returned
    // to the caller of the function.
    error InsufficientBalance(uint requested, uint available);

    // Sends an amount of existing coins
    // from any caller to an address
    function send(address receiver, uint amount) public {
        if (amount > balances[msg.sender])
            revert InsufficientBalance({
                requested: amount,
                available: balances[msg.sender]
            });

        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount);
    }
}
```

## Comunidad Honduras  
- Ethereum Honduras: https://linktr.ee/ethereumhn
- Ethereum Honduras Telegram: https://t.me/c/1901657551/1
- Ethereum Honduras Discord: https://discord.gg/zG3kfSdJtz
- Filosofia Codigo:
    - https://www.youtube.com/@FilosofiaCodigo/videos
    - https://dev.to/turupawn
 
## Otros Links
- Ethereum Website: https://ethereum.org/
- Documentación Solidity: https://soliditylang.org/
- Scroll website: https://scroll.io/

## Recomendaciones, Herramientas y Siguientes Pasos
- Solidity Academy de Alchemy: https://www.alchemy.com/university/courses/solidity
- Usar metodología de Test Driven Development: https://www.agilealliance.org/glossary/tdd/
- Instalar Solidity localmente: https://docs.soliditylang.org/en/v0.8.23/installing-solidity.html
- Scaffold ETH (Todo para empezar, perfecto para hackathons): https://scaffoldeth.io/
- Usar smart contract developer tools:
    - Hardhat (JS / TS): https://hardhat.org/
    - Foundry (Solidity): https://book.getfoundry.sh/
- Instalar plugin VSCode: https://github.com/juanfranblanco/vscode-solidity
- Aprender más de Ethereum: https://ethereum.org/es/developers/
- Lista de recursos de solidity: https://github.com/bkrem/awesome-solidity
- Lista de ejemplos: https://solidity-by-example.org/
- Crypto Zombies: https://cryptozombies.io/
- Desafios: https://github.com/kmjones1979/scaffold-eth-2-solidity/tree/main?utm_source=substack&utm_medium=email#readme
