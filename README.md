// libs/item/onboarding/PickupDeliverySelector.jsx
import React, { useState } from "react";
import PropTypes from "prop-types";
import { useTranslation } from "react-i18next";
import "./PickupDeliverySelector.css";

const PickupDeliverySelector = ({ defaultMode }) => {
  const [mode, setMode] = useState(defaultMode || "pickup");
  const { t } = useTranslation();

  return (
    <div className="pickup-delivery-selector">
      <button
        className={`option ${mode === "pickup" ? "active" : ""}`}
        onClick={() => setMode("pickup")}
      >
        {t("Pickup")}
      </button>
      <button
        className={`option ${mode === "delivery" ? "active" : ""}`}
        onClick={() => setMode("delivery")}
      >
        {t("Delivery")}
      </button>
    </div>
  );
};

PickupDeliverySelector.propTypes = {
  defaultMode: PropTypes.string,
};

export default PickupDeliverySelector;




.pickup-delivery-selector {
  display: flex;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.option {
  flex: 1;
  padding: 8px 16px;
  border: none;
  background: #f5f5f5;
  cursor: pointer;
}

.option.active {
  background: #0071dc;
  color: white;
  font-weight: bold;
}


import React from 'react';
import PickupDeliverySelector from './PickupDeliverySelector';

export default {
  title: 'Item/Onboarding/PickupDeliverySelector',
  component: PickupDeliverySelector,
};

const Template = (args) => <PickupDeliverySelector {...args} />;

export const Default = Template.bind({});
Default.args = {
  defaultMode: 'pickup'
};


import { render, screen, fireEvent } from '@testing-library/react';
import PickupDeliverySelector from './PickupDeliverySelector';

test('renders both Pickup and Delivery options', () => {
  render(<PickupDeliverySelector />);
  expect(screen.getByText('Pickup')).toBeInTheDocument();
  expect(screen.getByText('Delivery')).toBeInTheDocument();
});

test('defaults to Pickup', () => {
  render(<PickupDeliverySelector />);
  expect(screen.getByText('Pickup')).toHaveClass('active');
});

test('switches to Delivery on click', () => {
  render(<PickupDeliverySelector />);
  fireEvent.click(screen.getByText('Delivery'));
  expect(screen.getByText('Delivery')).toHaveClass('active');
});
