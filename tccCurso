/*
SPDX-License-Identifier: CC-BY-4.0
(c) Desenvolvido por Matheus Ricardo Tomas
This work is licensed under a Creative Commons Attribution 4.0 International License.
*/

pragma solidity 0.8.19;

import "https://github.com/jeffprestes/cursosolidity/blob/master/bradesco_token_aberto.sol";

contract TCCMatheus {

    Cliente private cliente;
    ExercicioToken private exercicioToken;

    struct Cliente {
        string primeiroNome;
        string sobreNome;
        address payable endereco; 
        bytes32 hashConta;       
        bool existe; 
    }

    constructor(string memory _primeiroNome,string memory _sobreNome,string memory _agencia, string memory _conta, address _enderecoToken) {
        string memory strTemp = string.concat(_agencia, _conta);
        bytes memory bTemp = bytes(strTemp);
        bytes32 hashTemp = keccak256(bTemp);

        cliente = Cliente(_primeiroNome, _sobreNome, payable(address(_enderecoToken)), hashTemp, true);
        exercicioToken = ExercicioToken(_enderecoToken);

    }

    function meuSaldo() public view returns(uint256) {
        return exercicioToken.balanceOf(address(this));
    }

    function gerarTokenParaEuCliente(uint256 _amount) public returns (bool){
        return exercicioToken.mint(address(this), _amount);
    }

}
