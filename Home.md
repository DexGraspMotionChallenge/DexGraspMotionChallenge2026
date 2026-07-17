# Dexterous Grasp Motion Challenge （HANDS Workshop@ECCV2026）

## **Challenge Overview**

Grasp motion generation for human-like multi-fingered hands has wide applications in animation, robotic /
grasping, mixed reality interaction, etc. Therefore, we design a grasp motion generation challenge that /
aims at producing physical plausible grasp motion trajectories conditioned on 3D objects.

The challenge is built on the [**GraspM3 dataset**](https://lihaoming45.github.io/GraspM3/index.html). 
We have retargeted this dataset to the LinkerHand O6, enabling the challenge to be conducted on the O6 hand. 
You can obtain the corresponding O6 dataset by filling out the [request form](https://forms.office.com/r/ZzCqsy7ft8).
An example for the training and testing of grasp motion generation will be provided prior to the challenge /
via github ([This Repository](https://github.com/DexGraspMotionChallenge/DexGraspMotionChallenge2026)). 

## **Important Dates**

- **Submission deadline** for results: September 14, 2026 (11:59PM PST)
- Results will be shared during the HANDS workshop at ECCV 2026

## **Rules**

- The evaluation process is conducted in Isaac Gym, and the test set objects are not visible to participants.
- Participants are allowed to adjust simulation parameters, provided they clearly specify all modifications made to the environment. However, please note that altering these parameters may compromise the integrity of the evaluation setup and could result in rollout failures.
- For fair comparisons, only methods trained using the datasets from this challenge are qualified for winning.
- Participants may not use the objects not in the dataset for training, fine-tuning, self-supervised pretraining, or any other form of method development.
- However, Participants may use the objects from the **Objaverse** dataset or other datasets to evaluate the algorithm before submission.
- **Participants are required to generate grasping sequences based on randomized initial hand poses.** The range of initial poses can be found in the **README.md** of this repository.

## **Dataset**

**Training Set**

- The objects for the challenge are from the **ShapeNet** dataset, which contains **5,048** objects and approximately **110,000** trajectory records.
- Each object was assigned a mass of 20 grams and a friction coefficient of 20. A fixed PID controller with preset parameters was used for control.

**Test Set**

- The challenge uses a subset of objects from the **Objaverse** dataset.  The distribution of the size of the testing objects is roughly the same with that of training objects.

## **Evaluation**

- The testing phase consists of an easy track and a hard track.
    - In the easy track, the mass and friction parameters are the same as those in the training environment: each object was assigned a mass of **20** grams and a friction coefficient of **20**.
    - In the hard track, the mass and the friction for each object are uniformly sampled from **[20grams, 200grams] and [1, 20].**
- By default, all grasps are initialized in the righthand side, at a random position **15–20** cm away. The palm is oriented toward the object to ensure proper approach direction. The orientation of the objects is uniformly randomized.
- Participants will be provided with training scripts, evaluation interfaces, and sample simulation pipelines to facilitate model development and evaluation.
- **A successful grasp is defined as lifting the object by 30 cm.**
- The grasp is also evaluated for human-likeness, quantified using an auto-encoder network adopted in  [Li et al., 2024; Pavlakos et al., 2019]. This auto-encoder is trained on  [Wang et al., 2023], and the human-likeness is measured by the mean per-joint position error (**MPJPE**) and smoothness error (**SE**), where lower values indicate more natural, human-like motions. 
- The smoothness of grasp trajectories is measured by the smoothness error (**SE**), defined as the average acceleration (L2-norm of second-order joint derivatives) across the trajectory.


## **Get Started**

- Please go to the [HANDS Workshop official page](https://hands-workshop.org/challenge2026.html) to register your team.
- Please fill out [this form](https://forms.office.com/r/ZzCqsy7ft8) to gain access to the dataset. The download link will automatically appear after you submit the form.
- An example for the training and testing of grasp motion generation can be found in [this repository](https://github.com/DexGraspMotionChallenge/DexGraspMotionChallenge2026).
- Participants are welcome to apply their own approaches in the challenge.

## **Submission Method**

Participants are required to submit following files：

- Model weight files
- Model inference code
- Documentation or instruction file

Results should be submitted via email. If the file size is too large, please provide an external download link.

Please send your submission to `ouyangwz@zju.edu.cn` and `xch118158@163.com` along with clear instructions for downloading the submission files. If you do not receive a response to your email after an extended period, please submit an issue via this repository.

## **Support**

Please report issues in our Github Repository or send email to `ouyangwz@zju.edu.cn` and `xch118158@163.com`.

## **Organizers**

![organizers_en](assets/organizers.png)



## **Citation**

```bibtex
@inproceedings{li2024tpgp,
  title={TPGP: Temporal-Parametric Optimization with Deep Grasp Prior for Dexterous Motion Planning},
  author={Li, Haoming and Ye, Qi and Huo, Yuchi and Liu, Qingtao and Jiang, Shijian and Zhou, Tao and Li, Xiang and Zhou, Yang and Chen, Jiming},
  booktitle={2024 IEEE International Conference on Robotics and Automation (ICRA)},
  pages={18106--18112},
  year={2024},
  organization={IEEE}
}

@inproceedings{pavlakos2019expressive,
  title={Expressive body capture: 3d hands, face, and body from a single image},
  author={Pavlakos, Georgios and Choutas, Vasileios and Ghorbani, Nima and Bolkart, Timo and Osman, Ahmed AA and Tzionas, Dimitrios and Black, Michael J},
  booktitle={Proceedings of the IEEE/CVF conference on computer vision and pattern recognition},
  pages={10975--10985},
  year={2019}
}

@inproceedings{wang2023dexgraspnet,
  title={Dexgraspnet: A large-scale robotic dexterous grasp dataset for general objects based on simulation},
  author={Wang, Ruicheng and Zhang, Jialiang and Chen, Jiayi and Xu, Yinzhen and Li, Puhao and Liu, Tengyu and Wang, He},
  booktitle={2023 IEEE International Conference on Robotics and Automation (ICRA)},
  pages={11359--11366},
  year={2023},
  organization={IEEE}
}
```


