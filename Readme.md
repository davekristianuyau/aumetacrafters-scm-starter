# Starter Next/Hardhat Project

After cloning the github, you will want to do the following to get the code running on your computer.

1. Inside the project directory, in the terminal type: npm i
2. Open two additional terminals in your VS code
3. In the second terminal type: npx hardhat node
4. In the third terminal, type: npx hardhat run --network localhost scripts/deploy.js
5. Back in the first terminal, type npm run dev to launch the front-end.

After this, the project will be running on your localhost. 
Typically at http://localhost:3000/


added 2 functions and frontend buttons for minting and burning to the connected address.

Assesment.sol

    function mint() public {
        require(msg.sender == owner, "You are not the owner of this account");

        // mint 1 ETH
        balance += amount;

        // emit the event
        emit Mint(msg.sender, 1 ether);
    }

    function burn() public {
        require(msg.sender == owner, "You are not the owner of this account");
        require(balance >= amount, "Insufficient funds to burn");

        // burn 1 ETH
        balance -= amount;

        // emit the event
        emit Withdraw(amount);
    }

index.js

    const mintETH = async () => {
      if (atm) {
        let tx = await atm.mint();
        await tx.wait();
        getBalance();
      }
    };

    const burnETH = async () => {
      if (atm) {
        let tx = await atm.withdraw(1);
        await tx.wait();
        getBalance();
      }
    };
