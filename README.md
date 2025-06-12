import i18n from 'i18next';
import { initReactI18next } from 'react-i18next';

i18n.use(initReactI18next).init({
  lng: 'en',
  fallbackLng: 'en',
  resources: {
    en: {
      translation: {
        extraSavings: {
          showDiscountInfo: 'Show Extra Discount Info',
          modalTitle: 'Show Extra Discount Info',
          modalDescription: 'Extra discount details',
          save20: 'Save an extra 20% on your first purchase!',
          terms: 'Only applicable on eligible items. Terms apply.'
        },
        common: {
          close: 'Close'
        }
      }
    }
  }
});

export default i18n;





import React from 'react';
import { ExtraSavingsModal } from './extra-savings-modal.component';
import { I18nextProvider } from 'react-i18next';
import i18n from './i18n'; // make sure this path matches

export default {
  title: 'Item/ExtraSavingsModal',
  component: ExtraSavingsModal,
};

export const Default = () => (
  <I18nextProvider i18n={i18n}>
    <ExtraSavingsModal />
  </I18nextProvider>
);
