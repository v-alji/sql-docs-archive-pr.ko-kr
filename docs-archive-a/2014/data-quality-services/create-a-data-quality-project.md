---
title: 데이터 품질 프로젝트 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.newdqproject.f1
helpviewer_keywords:
- create,data quality project
- data quality project,create
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3bab14b34123464450bcf0de7540364fc642343e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728707"
---
# <a name="create-a-data-quality-project"></a><span data-ttu-id="d4761-102">데이터 품질 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="d4761-102">Create a Data Quality Project</span></span>
  <span data-ttu-id="d4761-103">이 항목에서는 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]를 사용하여 데이터 품질 프로젝트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-103">This topic describes how to create a data quality project by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="d4761-104">데이터 품질 프로젝트는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 정리 또는 일치 작업을 실행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-104">A data quality project is used to run the cleansing or matching activity in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d4761-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d4761-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d4761-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="d4761-106">Prerequisites</span></span>  
 <span data-ttu-id="d4761-107">데이터 품질 프로젝트에서 정리 및 일치 작업을 수행하는 데 사용할 관련 기술 자료가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-107">You must have a relevant knowledge base to use in the data quality project for the cleansing or matching activity.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d4761-108">보안</span><span class="sxs-lookup"><span data-stu-id="d4761-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d4761-109">권한</span><span class="sxs-lookup"><span data-stu-id="d4761-109">Permissions</span></span>  
 <span data-ttu-id="d4761-110">데이터 품질 프로젝트를 만들려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_kb_operator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-110">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to create a data quality project.</span></span>  
  
##  <a name="create-a-data-quality-project"></a><a name="Create"></a><span data-ttu-id="d4761-111">데이터 품질 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="d4761-111">Create a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="d4761-112">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="d4761-113">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **새 데이터 품질 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New data quality project**.</span></span>  
  
3.  <span data-ttu-id="d4761-114">**새 데이터 품질 프로젝트** 화면에서</span><span class="sxs-lookup"><span data-stu-id="d4761-114">In the **New Data Quality Project** screen:</span></span>  
  
    1.  <span data-ttu-id="d4761-115">**이름** 상자에 새 데이터 품질 프로젝트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-115">In the **Name** box, type a name for the new data quality project.</span></span>  
  
    2.  <span data-ttu-id="d4761-116">(옵션) **설명** 상자에 새 데이터 품질 프로젝트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-116">(Optional) In the **Description** box, type a description for the new data quality project.</span></span>  
  
    3.  <span data-ttu-id="d4761-117">**기술 자료 사용** 목록에서 데이터 품질 프로젝트에 사용할 기술 자료를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-117">In the **Use Knowledge base** list, click to select a knowledge base to be used for the data quality project.</span></span> <span data-ttu-id="d4761-118">오른쪽 **기술 자료 정보: <Knowledge_Base_Name>** 영역에 선택한 기술 자료에서 사용할 수 있는 도메인 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-118">The **Knowledge base details: <Knowledge_Base_Name>** area on the right side displays the domain names available in the selected knowledge base.</span></span>  
  
    4.  <span data-ttu-id="d4761-119">**작업 선택** 영역에서 이 데이터 품질 프로젝트를 사용하여 수행할 작업을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-119">In the **Select Activity** area, click on an activity that you want to perform using this data quality project:</span></span>  
  
        -   <span data-ttu-id="d4761-120">**정리**: 원본 데이터를 정리하려면 이 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-120">**Cleansing**: Select this activity to cleanse the source data.</span></span>  
  
        -   <span data-ttu-id="d4761-121">**일치**: 일치를 수행하려면 이 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-121">**Matching**: Select this activity to perform matching.</span></span> <span data-ttu-id="d4761-122">데이터 품질 프로젝트를 위해 선택한 기술 자료에 일치 정책이 포함된 경우에만 이 작업을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-122">This activity is available only if the knowledge base selected for the data quality project contains a matching policy.</span></span>  
  
4.  <span data-ttu-id="d4761-123">**만들기** 를 클릭하여 데이터 품질 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-123">Click **Create** to create a data quality project.</span></span>  
  
##  <a name="follow-up-after-creating-a-data-quality-project"></a><a name="FollowUp"></a> <span data-ttu-id="d4761-124">후속 작업: 데이터 품질 프로젝트를 만든 후</span><span class="sxs-lookup"><span data-stu-id="d4761-124">Follow Up: After Creating a Data Quality Project</span></span>  
 <span data-ttu-id="d4761-125">데이터 품질 프로젝트를 만든 후에는 선택한 작업(정리 또는 일치)을 수행하는 데 사용할 마법사가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d4761-125">After you create a data quality project, you are presented with a wizard that you use to perform the selected activity: cleansing or matching.</span></span> <span data-ttu-id="d4761-126">정리 및 일치 작업에 대한 자세한 내용은 [데이터 정리](../../2014/data-quality-services/data-cleansing.md) 및 [데이터 일치](../../2014/data-quality-services/data-matching.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4761-126">For more information about the cleansing and matching activities, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md) and [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
