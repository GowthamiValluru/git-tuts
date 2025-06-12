import React, { useState } from 'react';
import Modal from '@mui/material/Modal';
import Box from '@mui/material/Box';
import Button from '@mui/material/Button';
import Typography from '@mui/material/Typography';

const style = {
  position: 'absolute' as const,
  top: '50%',
  left: '50%',
  transform: 'translate(-50%, -50%)',
  bgcolor: 'background.paper',
  border: '1px solid #ccc',
  boxShadow: 24,
  p: 4,
  borderRadius: '10px'
};

export const ExtraSavingsModal = () => {
  const [open, setOpen] = useState(false);

  const handleOpen = () => {
    console.log('Beacon: Modal opened');
    setOpen(true);
  };

  const handleClose = () => setOpen(false);

  return (
    <div>
      <Button onClick={handleOpen} variant="contained" aria-label="Show Extra Discount Info">
        Show Extra Discount Info
      </Button>
      <Modal
        open={open}
        onClose={handleClose}
        aria-labelledby="extra-savings-title"
        aria-describedby="extra-savings-description"
      >
        <Box sx={style}>
          <Typography id="extra-savings-title" variant="h6" component="h2">
            Save an extra 20% on your first purchase!
          </Typography>
          <Typography id="extra-savings-description" sx={{ mt: 2 }}>
            Only applicable on eligible items. Terms apply.
          </Typography>
          <Button onClick={handleClose} sx={{ mt: 2 }} variant="outlined">
            Close
          </Button>
        </Box>
      </Modal>
    </div>
  );
};





import React from 'react';
import { ExtraSavingsModal } from './extra-savings-modal.component';

export default {
  title: 'Item/ExtraSavingsModal',
  component: ExtraSavingsModal,
};

export const Default = () => <ExtraSavingsModal />;
