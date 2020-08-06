---
title: '2 단원: Suppliers 기술 자료를 사용 하 여 공급자 데이터 정리 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ebc0231cd0f28fcad23656cf22abd8d68eca7dc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639172"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a><span data-ttu-id="ef6d3-102">2단원: 공급자 기술 자료를 사용하여 공급자 데이터 정리</span><span class="sxs-lookup"><span data-stu-id="ef6d3-102">Lesson 2: Cleansing Supplier Data using the Suppliers Knowledge Base</span></span>
  <span data-ttu-id="ef6d3-103">이 단원에서는 첫 번째 단원에서 만든 **Suppliers** 기술 자료를 사용해서 Excel 파일에서 공급자 데이터를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-103">In this lesson, you cleanse the supplier data in an Excel file by using the **Suppliers** knowledge base you have created in the first lesson.</span></span> <span data-ttu-id="ef6d3-104">DQS의 데이터 정리에는 데이터가 기술 자료의 지식을 준수하는 정도를 분석하는 **컴퓨터 기반 프로세스** 및 컴퓨터 기반 프로세스 결과를 검토하고 수정할 수 있게 해주는 **대화형 프로세스** 가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-104">Data cleansing in DQS includes a **computer-assisted process** that analyzes how data conforms to the knowledge in a knowledge base, and an **interactive process** that enables you to review and modify results from the computer-assisted process.</span></span> <span data-ttu-id="ef6d3-105">데이터 정리 기능은 데이터 원본에 포함된 잘못된 데이터를 식별한 후 잘못된 데이터를 수정하거나 수정을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-105">The data cleansing feature identifies incorrect data in your data source and then corrects or suggests corrections for the incorrect data.</span></span> <span data-ttu-id="ef6d3-106">또한 도메인 값, 동의어의 선행 값, 도메인 규칙, 용어 기반 관계 및 참조 데이터를 사용해서 고객 데이터를 표준화 및 강화합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-106">It also standardizes and enriches customer data by using domain values, leading values for synonyms, domain rules, term-based relations, and reference data.</span></span> <span data-ttu-id="ef6d3-107">컴퓨터 기반 프로세스로 제안된 변경 사항은 대화형으로 승인 또는 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-107">You can interactively approve or reject changes proposed by the computer-assisted process.</span></span> <span data-ttu-id="ef6d3-108">자세한 내용은 [데이터 정리](https://msdn.microsoft.com/library/gg524800.aspx) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-108">See [Data Cleansing](https://msdn.microsoft.com/library/gg524800.aspx) for more details.</span></span>  
  
 <span data-ttu-id="ef6d3-109">컴퓨터 기반 프로세스에는 DQS 클라이언트 기본 페이지에서 구성 옵션을 사용하여 구성할 수 있는 다음과 같은 임계값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-109">The computer-assisted process uses the following threshold values that you can configure using the Configuration option on the DQS Client main page.</span></span>  
  
-   <span data-ttu-id="ef6d3-110">**제안 최소 점수:** DQS에서 대체 값을 제안하기 위해 사용되는 최소 점수 또는 신뢰도 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-110">**Min score for suggestions:** The minimum score or confidence level that is used by DQS for suggesting replacement for a value.</span></span>  
  
-   <span data-ttu-id="ef6d3-111">**자동 수정 최소 점수:** DQS에서 값을 자동으로 수정하기 위해 사용되는 최소 점수 또는 신뢰도 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-111">**Min score for auto corrections:** The minimum score or confidence level that is used by DQS for automatically correcting a value.</span></span>  
  
 <span data-ttu-id="ef6d3-112">이러한 설정을 구성하는 방법에 대한 자세한 내용은 [정리 및 일치에 대한 임계값 구성](https://msdn.microsoft.com/library/hh510415.aspx) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-112">See [Configure Threshold Values for Cleansing and Matching](https://msdn.microsoft.com/library/hh510415.aspx) for details on how to configure these settings.</span></span>  
  
 <span data-ttu-id="ef6d3-113">이 단원에서는 Suppliers 기술 자료를 사용해서 입력 데이터를 정리하기 위해 다음과 같은 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-113">In this lesson, you perform the following tasks to cleanse the input data by using the Suppliers knowledge base.</span></span>  
  
1.  <span data-ttu-id="ef6d3-114">정리를 위한 데이터 품질 프로젝트를 만들고, Excel 파일에서 원본 데이터를 분석 및 정리하기 위해 사용할 기술 자료로 Suppliers 기술 자료를 선택하고, 정리 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-114">Create a Data Quality Project for Cleansing, select the Suppliers knowledge base as the knowledge base to use to analyze and cleanse the source data in an Excel file, and select the Cleansing activity.</span></span>  
  
2.  <span data-ttu-id="ef6d3-115">정리할 Excel 열을 기술 자료에서 적합한 DQS 도메인/복합 도메인에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-115">Map the Excel columns that you want to cleanse to appropriate DQS domains/composite domains in the knowledge base.</span></span>  
  
3.  <span data-ttu-id="ef6d3-116">컴퓨터 기반 정리 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-116">Run the computer-assisted cleansing activity.</span></span> <span data-ttu-id="ef6d3-117">컴퓨터 기반 프로세스에서는 Data Quality 클라이언트에 데이터를 대화형으로 정리하기 위해 사용할 수 있는 데이터 품질 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-117">The computer-assisted process displays data quality information in the Data Quality Client that you can use to cleanse the data interactively.</span></span>  
  
4.  <span data-ttu-id="ef6d3-118">정리 작업의 결과를 보고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-118">View and manage the results of the cleansing activity.</span></span> <span data-ttu-id="ef6d3-119">컴퓨터 기반 프로세스에서 찾은 올바른 값, 잘못되었지만 수정된 값, 변경 값이 제안된 잘못된 값 또는 올바르지 않은 값을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-119">You can review the values that the computer-assisted process finds to be correct, incorrect but corrected, incorrect with a suggested change, or invalid.</span></span> <span data-ttu-id="ef6d3-120">변경 사항을 대화형으로 승인 또는 거부하고, 다음으로 수정 필드를 사용해서 컴퓨터 기반 프로세스의 제안을 수정하거나 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-120">You can interactively approve or reject changes, correcting or overriding the suggestion from the computer-assisted process by using the Correct To field.</span></span>  
  
5.  <span data-ttu-id="ef6d3-121">정리 프로세스의 결과를 Excel 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-121">Export the results from the cleansing process to an Excel file.</span></span>  
  
6.  <span data-ttu-id="ef6d3-122">정리 프로젝트의 값을 도메인으로 가져와서 기술 자료의 정보를 새로운 규칙, 값, 수정 등으로 보강 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef6d3-122">Import the values from the cleansing project into domains to augment the knowledge in the knowledge base with new rules, values, corrections etc...</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ef6d3-123">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ef6d3-123">Next Step</span></span>  
 [<span data-ttu-id="ef6d3-124">태스크 1: 데이터 품질 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="ef6d3-124">Task 1: Creating a Data Quality Project</span></span>](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  
