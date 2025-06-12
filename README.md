import React, { useState } from 'react';
import { useTranslation } from 'react-i18next';
import { Button, Modal } from '@mui/material'; // assuming you're using MUI

const style = {
  borderRadius: "10px",
};

export const ExtraSavingsModal = () => {
  const [open, setOpen] = useState(false);
  const { t } = useTranslation();

  const handleOpen = () => {
    if (process.env.NODE_ENV === 'development') {
      console.log("Beacon: Modal opened");
    }
    setOpen(true);
  };

  const handleClose = () => {
    setOpen(false);
  };

  return (
    <div>
      <Button
        onClick={handleOpen}
        variant="contained"
        aria-label={t('extraSavings.showDiscountInfo')}
      >
        {t('extraSavings.showDiscountInfo')}
      </Button>

      <Modal
        open={open}
        onClose={handleClose}
        aria-labelledby={t('extraSavings.modalTitle')}
        aria-describedby={t('extraSavings.modalDescription')}
      >
        <div style={style}>
          <h2>{t('extraSavings.save20')}</h2>
          <p>{t('extraSavings.terms')}</p>
          <Button onClick={handleClose}>{t('common.close')}</Button>
        </div>
      </Modal>
    </div>
  );
};




import React from 'react';
import { ExtraSavingsModal } from './extra-savings-modal.component';
import { I18nextProvider } from 'react-i18next';
import i18n from '../../../i18n'; // adjust this import path based on your project

export default {
  title: 'Item/ExtraSavingsModal',
  component: ExtraSavingsModal,
};

export const Default = () => (
  <I18nextProvider i18n={i18n}>
    <ExtraSavingsModal />
  </I18nextProvider>
);

