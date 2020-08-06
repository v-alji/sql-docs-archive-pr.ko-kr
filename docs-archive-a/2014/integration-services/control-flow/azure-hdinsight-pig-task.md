---
title: Azure HDInsight Pig 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afppigtask.f1
- sql11.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 214db5e83272b1fa70c9e70eef8f8b9a43bac095
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648495"
---
# <a name="azure-hdinsight-pig-task"></a><span data-ttu-id="0e23b-102">Azure HDInsight Pig 태스크</span><span class="sxs-lookup"><span data-stu-id="0e23b-102">Azure HDInsight Pig Task</span></span>
<span data-ttu-id="0e23b-103">**Azure HDInsight Pig 태스크** 를 사용하여 Azure HDInsight 클러스터에서 Pig 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-103">Use the **Azure HDInsight Pig Task** to run Pig script on an Azure HDInsight cluster.</span></span>
     
<span data-ttu-id="0e23b-104">**Azure HDInsight Pig 태스크**를 추가하려면 해당 태스크를 SSIS 디자이너로 끌어서 놓고 두 번 클릭하거나 마우스 오른쪽 단추를 클릭하고 **편집** 을 클릭하여 다음과 같은 **Azure HDInsight Pig 태스크 편집기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-104">To add an **Azure HDInsight Pig Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Pig Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="0e23b-105">다음 목록에서는 이 대화 상자의 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-105">The following list describes fields in this dialog box.</span></span>  
  
1.  <span data-ttu-id="0e23b-106">**HDInsightConnection** 필드에서는 기존 Azure HDInsight 연결 관리자를 선택하거나 스크립트를 실행하는 데 사용한 Azure HDInsight 클러스터를 참조하는 HDInsight 연결 관리자를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-106">For the **HDInsightConnection** field, select an existing Azure HDInsight Connection Manager or create a new one that refers to the Azure HDInsight cluster used to execute the script.</span></span>
  
2.  <span data-ttu-id="0e23b-107">**AzureStorageConnection** 필드에서는 기존 Azure Storage 연결 관리자를 선택하거나 클러스터에 연결된 Azure Storage 계정을 참조하는 Storage 연결 관리자를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-107">For the **AzureStorageConnection** field, select an existing Azure Storage Connection Manager or create a new one that refers to the Azure Storage Account associated with the cluster.</span></span> <span data-ttu-id="0e23b-108">스크립트 실행 출력 및 오류 로그를 다운로드하려는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-108">This is only necessary if you want to download the script execution output and error logs.</span></span>
 
3.  <span data-ttu-id="0e23b-109">**BlobContainer** 필드의 경우 클러스터와 연결된 스토리지 컨테이너 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-109">For the **BlobContainer** field, specify the storage container name associated with the cluster.</span></span> <span data-ttu-id="0e23b-110">스크립트 실행 출력 및 오류 로그를 다운로드하려는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-110">This is only necessary if you want to download the script execution output and error logs.</span></span>
  
4.  <span data-ttu-id="0e23b-111">**LocalLogFolder** 필드의 경우 스크립트 실행 출력 및 오류 로그를 다운로드할 폴더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-111">For the **LocalLogFolder** field, specify the folder to which the script execution output and error logs will be downloaded to.</span></span> <span data-ttu-id="0e23b-112">스크립트 실행 출력 및 오류 로그를 다운로드하려는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-112">This is only necessary if you want to download the script execution output and error logs.</span></span>   
  
5.  <span data-ttu-id="0e23b-113">두 가지 방법으로 실행할 Pig 스크립트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-113">There are two ways to specify the Pig script to execute:</span></span>
  
    1.  <span data-ttu-id="0e23b-114">**인라인 스크립트**: **스크립트 입력** 대화 상자에 실행할 인라인 스크립트를 입력하여 **스크립트** 필드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-114">**In-line script**: Specify the **Script** field by typing in-line the script to execute in the **Enter Script** dialog box.</span></span>
  
    2.  <span data-ttu-id="0e23b-115">**스크립트 파일**: Azure Blob Storage에 스크립트 파일을 업로드하고 **BlobName** 필드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-115">**Script file**: Upload the script file to Azure Blob Storage and specify the **BlobName** field.</span></span> <span data-ttu-id="0e23b-116">blob이 기본 스토리지 계정 또는 HDInsight 클러스터와 연결된 컨테이너에 없는 경우 **ExternalStorageAccountName** 및 **ExternalBlobContainer** 필드를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-116">If the blob is not in the default storage account or container associated with the HDInsight cluster, the **ExternalStorageAccountName** and **ExternalBlobContainer** fields must be specified.</span></span> <span data-ttu-id="0e23b-117">외부 Blob의 경우에는 공용으로 액세스할 수 있도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-117">For an external blob, make sure that it is configured as publicly accessible.</span></span>  
  
     <span data-ttu-id="0e23b-118">스크립트 파일과 인라인 스크립트를 모두 지정하면 스크립트 파일이 사용되며 인라인 스크립트는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e23b-118">If both are specified, script file will be used and the in-line script will be ignored.</span></span>
