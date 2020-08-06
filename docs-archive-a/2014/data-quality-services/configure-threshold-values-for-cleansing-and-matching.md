---
title: 정리 및 일치에 대한 임계값 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0faf64e96468a3a9aac0de12d3ec3acbb1e1ed85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728723"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a><span data-ttu-id="272f5-102">정리 및 일치에 대한 임계값 구성</span><span class="sxs-lookup"><span data-stu-id="272f5-102">Configure Threshold Values for Cleansing and Matching</span></span>
  <span data-ttu-id="272f5-103">이 항목에서는 컴퓨터 기반 정리 및 일치 작업 중에 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 사용할 임계값을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-103">This topic describes how to configure threshold values that will be used during the computer-assisted cleansing and matching activities in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="272f5-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="272f5-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="272f5-105">보안</span><span class="sxs-lookup"><span data-stu-id="272f5-105">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="272f5-106">권한</span><span class="sxs-lookup"><span data-stu-id="272f5-106">Permissions</span></span>  
 <span data-ttu-id="272f5-107">이러한 임계값을 구성하려면 DQS_MAIN 데이터베이스에 대한 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-107">You must have the dqs_administrator role on the DQS_MAIN database to configure these threshold values.</span></span>  
  
##  <a name="configuring-the-threshold-values"></a><a name="Configure"></a> <span data-ttu-id="272f5-108">임계값 구성</span><span class="sxs-lookup"><span data-stu-id="272f5-108">Configuring the Threshold Values</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="272f5-109">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-109">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="272f5-110">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-110">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="272f5-111">그런 다음 **일반 설정** 탭을 클릭 합니다. 이 탭에서 정리 및 일치 작업에 대 한 임계값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-111">Next, click the **General Settings** tab. This tab enables you to specify threshold values for cleansing as well as matching activities.</span></span>  
  
4.  <span data-ttu-id="272f5-112">정리 작업에 대한 임계값을 지정하려면 **대화형 정리** 영역 아래의 다음 상자에 적절한 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-112">To specify threshold values for the cleansing activity, specify appropriate values in the following boxes under the **Interactive Cleansing** area:</span></span>  
  
    -   <span data-ttu-id="272f5-113">**제안 최소 점수**: 컴퓨터 기반 정리 프로세스 중에 DQS에서 대체 값을 제안하는 데 사용할 최소 점수 또는 신뢰도 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-113">**Min score for suggestions**: The minimum score or the confidence level that will be used by DQS for suggesting replacements for a value during the computer-assisted cleansing process.</span></span> <span data-ttu-id="272f5-114">해당 백분율 값의 10진수 표기법으로 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-114">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="272f5-115">예를 들어 75%의 경우 0.75를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-115">For example, type 0.75 for 75%.</span></span> <span data-ttu-id="272f5-116">이 값은 **자동 수정 최소 점수** 상자에 지정된 값보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-116">This value should be less than or equal to the value specified in the **Min score for auto corrections** box.</span></span> <span data-ttu-id="272f5-117">기본값은 0.7입니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-117">The default value is 0.7.</span></span>  
  
    -   <span data-ttu-id="272f5-118">**자동 수정 최소 점수**: 컴퓨터 기반 정리 프로세스 중에 DQS에서 값을 자동으로 수정하는 데 사용할 최소 점수 또는 신뢰도 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-118">**Min score for auto corrections**: The minimum score or the confidence level that will be used by DQS for automatically correcting a value during the computer-assisted cleansing process.</span></span> <span data-ttu-id="272f5-119">해당 백분율 값의 10진수 표기법으로 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-119">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="272f5-120">예를 들어 90%의 경우 0.9를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-120">For example, enter 0.9 for 90%.</span></span> <span data-ttu-id="272f5-121">기본값은 0.8입니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-121">The default value is 0.8.</span></span>  
  
5.  <span data-ttu-id="272f5-122">일치 작업에 대한 임계값을 지정하려면 **일치** 영역 아래의 **최소 레코드 점수** 상자에 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-122">To specify threshold value for the matching activity, specify a value in the **Min record score** box under the **Matching** area.</span></span> <span data-ttu-id="272f5-123">이 값은 레코드가 다른 레코드와 일치하는 것으로 간주되는 최소 점수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-123">This value signifies the minimum score for a record to be considered as a match for another record.</span></span> <span data-ttu-id="272f5-124">기본값은 80%입니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-124">The default value is 80%.</span></span>  
  
6.  <span data-ttu-id="272f5-125">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="272f5-125">Click **Close**.</span></span>  
  
  
