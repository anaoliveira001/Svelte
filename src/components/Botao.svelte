<button type="submit" class="botao">
    <slot></slot>
  </button>
  
  <style>
    .botao {
      padding: 15px 24px;
      border-radius: 8px;
      border: none;
      background: #8515d5;
      line-height: 26px;
      color: #fff;
      font-size: 22px;
      cursor: pointer;
  
      transition: background-color 0.2s;
  
      display: flex;
      align-items: center;
      gap: 13px;
    }
  
    .botao:hover {
      background: #d26ad5;
    }
  </style>