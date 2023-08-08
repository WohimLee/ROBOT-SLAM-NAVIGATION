# 1 Converter
- 包含在 ORB_SLAM2 命名空间
```c++
namespace ORB_SLAM2
{    
}
```

>头文件
```c++
#include<opencv2/core/core.hpp>

#include<Eigen/Dense>
#include"Thirdparty/g2o/g2o/types/types_six_dof_expmap.h"
#include"Thirdparty/g2o/g2o/types/types_seven_dof_expmap.h"
```

# class Converter
## public

### 函数
>描述子矩阵到单行的描述子向量的转换
```c++
static std::vector<cv::Mat> toDescriptorVector(
    const cv::Mat &Descriptors);
/**
 * cv::Mat -> std::vector<cv::Mat>
 * 转换后的结果就是吧cv::Mat的每一行直接串联起来。
 * 
 * 属性：Descriptors: 待转换的描述子
 * 返回值：std::vector<cv::Mat> 转换结果
 * 
 * 应当注意，这里的描述子矩阵是多个单行的cv::Mat组成的。
 */

```

```c++
/**
 * @name toSE3Quat
 * @details 将不同格式存储的位姿统一转换成为g2o::SE3Quat格式存储
 * @{
 */

/**
 * @brief 将以cv::Mat格式存储的位姿转换成为g2o::SE3Quat类型
 * 
 * @param[in] 以cv::Mat格式存储的位姿
 * @return g2o::SE3Quat 将以g2o::SE3Quat格式存储的位姿
 */
static g2o::SE3Quat toSE3Quat(const cv::Mat &cvT);
```

```c++
/**
 * @brief 将以g2o::Sim3格式存储的位姿转换成为g2o::SE3Quat类型
 * 
 * @param[in] gSim3 以g2o::Sim3格式存储的位姿
 * @return g2o::SE3Quat 
 */
static g2o::SE3Quat toSE3Quat(const g2o::Sim3 &gSim3);

/** @} */

/**
 * @name toCvMat \n
 * @details 将各种格式转换成为cv::Mat存储
 * @{
 */

/**
 * @brief 将以g2o::SE3Quat格式存储的位姿转换成为cv::Mat格式
 * 
 * @param[in] SE3 输入的g2o::SE3Quat格式存储的、待转换的位姿
 * @return cv::Mat 转换结果
 * @remark 
 */
static cv::Mat toCvMat(const g2o::SE3Quat &SE3);
/**
 * @brief 将以g2o::Sim3格式存储的位姿转换成为cv::Mat格式
 * 
 * @param[in] Sim3 输入的g2o::Sim3格式存储的、待转换的位姿
 * @return cv::Mat 转换结果
 * @remark
 */
static cv::Mat toCvMat(const g2o::Sim3 &Sim3);
/**
 * @brief 将4x4 double型Eigen矩阵存储的位姿转换成为cv::Mat格式
 * 
 * @paramp[in] m 输入Eigen矩阵
 * @return cv::Mat 转换结果
 * @remark
 */
static cv::Mat toCvMat(const Eigen::Matrix<double,4,4> &m);
/**
 * @brief 将一个3x1的Eigen行向量转换成为cv::Mat格式
 * 
 * @param[in] m 3x1的Eigen行向量
 * @return cv::Mat 转换结果
 */
static cv::Mat toCvMat(const Eigen::Matrix3d &m);
/**
 * @brief 将一个3x1的Eigen行向量转换成为cv::Mat格式
 * 
 * @param[in] m 3x1的Eigen行向量
 * @return cv::Mat 转换结果
 */
static cv::Mat toCvMat(const Eigen::Matrix<double,3,1> &m);
/**
 * @brief 将给定的旋转矩阵和平移向量转换为以cv::Mat存储的李群SE3
 * @details 其实就是组合旋转矩阵和平移向量来构造SE3
 * @param[in] R 旋转矩阵
 * @param[in] t 平移向量
 * @return cv::Mat 李群SE3
 */
static cv::Mat toCvSE3(const Eigen::Matrix<double,3,3> &R, const Eigen::Matrix<double,3,1> &t);
/** @} */


/**
 * @name toEigen
 * @details 将给出的数据以Eigen库中对应的数据类型存储
 * @{
 */

/**
 * @brief 将cv::Mat类型数据转换成为3x1的Eigen矩阵
 * 
 * @param[in] cvVector 待转换的数据
 * @return Eigen::Matrix<double,3,1> 转换结果
 * @note 需要确保输入的数据大小尺寸正确。
 */
static Eigen::Matrix<double,3,1> toVector3d(const cv::Mat &cvVector);
/**
 * @brief 将cv::Point3f转换成为Eigen中3x1的矩阵
 * 
 * @param[in] cvPoint 输入的cv表示的三维点坐标
 * @return Eigen::Matrix<double,3,1> 以Eigen中3x1向量表示的三维点坐标
 */
static Eigen::Matrix<double,3,1> toVector3d(const cv::Point3f &cvPoint);
/**
 * @brief 将一个3x3的cv::Mat矩阵转换成为Eigen中的矩阵
 * 
 * @param[in] cvMat3 输入
 * @return Eigen::Matrix<double,3,3> 转换结果
 */
static Eigen::Matrix<double,3,3> toMatrix3d(const cv::Mat &cvMat3);
/**
 * @brief 将给定的cv::Mat类型的旋转矩阵转换成以std::vector<float>类型表示的四元数
 * 
 * @param[in] M 以cv::Mat表示的旋转矩阵
 * @return std::vector<float> 四元数
 * @note 需要自己保证参数M满足旋转矩阵的定义
 * @remark
 */
static std::vector<float> toQuaternion(const cv::Mat &M);
```
