import React, { useState } from "react";

const Calculator = () => {
  const [input, setInput] = useState("");
  const [explanation, setExplanation] = useState("");

  const handleClick = (value) => {
    setInput((prev) => prev + value);
    setExplanation("");
  };

  const handleClear = () => {
    setInput("");
    setExplanation("");
  };

  const handleEqual = () => {
    try {
      const result = eval(input);
      setExplanation(`${input} = ${result}`);
      setInput(result.toString());
    } catch (error) {
      setInput("Erro");
      setExplanation("");
    }
  };

  return (
    <div className="max-w-sm mx-auto mt-10 p-4 bg-black text-white rounded-3xl shadow-lg border border-white">
      <div className="mb-2 text-right text-2xl border rounded-2xl p-2 bg-gray-800 text-white">
        {input || "0"}
      </div>
      {explanation && (
        <div className="mb-4 text-sm text-gray-400 text-right italic">
          {explanation}
        </div>
      )}
      <div className="grid grid-cols-4 gap-2">
        {["7", "8", "9", "/",
          "4", "5", "6", "*",
          "1", "2", "3", "-",
          "0", ".", "C", "+"].map((btn) => (
          <button
            key={btn}
            onClick={() => btn === "C" ? handleClear() : handleClick(btn)}
            className="bg-gray-700 hover:bg-gray-600 text-white rounded-2xl p-4 text-xl border border-white"
          >
            {btn}
          </button>
        ))}
        <button
          onClick={handleEqual}
          className="col-span-4 bg-white hover:bg-gray-200 text-black rounded-2xl p-4 text-xl border border-white"
        >
          =
        </button>
      </div>
      <p className="text-center text-sm text-white mt-4">© 2025 Heitor de Assis. Todos os direitos reservados.</p>
    </div>
  );
};

export default Calculator;
