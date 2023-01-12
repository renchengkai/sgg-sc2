# Train frcnn
script: ```CUDA_VISIBLE_DEVICES=2,3,4,5 python -m torch.distributed.launch --master_port 10001 --nproc_per_node=4 tools/detector_pretrain_net.py --config-file "configs/e2e_relation_detector_X_101_32_8_FPN_1x.yaml" SOLVER.IMS_PER_BATCH 16 TEST.IMS_PER_BATCH 8 SOLVER.MAX_ITER 5000 SOLVER.STEPS "(3000, 4500)" SOLVER.VAL_PERIOD 2000 SOLVER.CHECKPOINT_PERIOD 2000 MODEL.RELATION_ON False OUTPUT_DIR checkpoints/sc2-frcnn SOLVER.PRE_VAL False```

# Train imp sggdet
script: ```CUDA_VISIBLE_DEVICES=4,5 python -m torch.distributed.launch --master_port 10025 --nproc_per_node=2 tools/relation_train_net.py --config-file "configs/e2e_relation_X_101_32_8_FPN_1x.yaml" MODEL.ROI_RELATION_HEAD.USE_GT_BOX False MODEL.ROI_RELATION_HEAD.USE_GT_OBJECT_LABEL False MODEL.ROI_RELATION_HEAD.PREDICTOR IMPPredictor SOLVER.IMS_PER_BATCH 12 TEST.IMS_PER_BATCH 2 DTYPE "float16" SOLVER.MAX_ITER 50000 SOLVER.VAL_PERIOD 2000 SOLVER.CHECKPOINT_PERIOD 2000 GLOVE_DIR glove MODEL.PRETRAINED_DETECTOR_CKPT checkpoints/sc2-frcnn/model_final.pth OUTPUT_DIR checkpoints/sc2-imp```

# Test imp sggdet
script: ```CUDA_VISIBLE_DEVICES=5 python -m torch.distributed.launch --master_port 10027 --nproc_per_node=1 tools/relation_test_net.py --config-file "configs/e2e_relation_X_101_32_8_FPN_1x.yaml" MODEL.ROI_RELATION_HEAD.USE_GT_BOX False MODEL.ROI_RELATION_HEAD.USE_GT_OBJECT_LABEL False MODEL.ROI_RELATION_HEAD.PREDICTOR IMPPredictor TEST.IMS_PER_BATCH 1 DTYPE "float16" GLOVE_DIR glove MODEL.PRETRAINED_DETECTOR_CKPT checkpoints/sc2-imp/model_0006000.pth OUTPUT_DIR checkpoints/sc2-imp TEST.CUSTUM_EVAL True TEST.CUSTUM_PATH ../images DETECTED_SGG_DIR ../sggtest```


------------

# prepare sggdata

1. put those files into ```DIR``` 'genrateData'
   - relationships.json
   - image_data.json
   - object_alias.txt
   - object_list.txt
   - objects.json
   - predicate_alias.txt
   - predicate_list.txt
2. run sh script ```create_roidb.sh``` to get
   - VG-SGG.h5
   - VG-SGG-dicts.json
3. put those files into ```DIR``` 'genrateData/with_attri'
   - attribute_synsets.json
   - attributes.json
4. run python script ```generator.py``` to get
   - VG-SGG-dicts-with-attri.json
   - VG-SGG-with-attri.h5
5. put those files into ```DIR``` 'datasets/vg'
   - image_data.json
   - VG-SGG-dicts-with-attri.json
   - VG-SGG-with-attri.h5
6. put all images data into ```dir``` 'datasets/vg/VG_100K'