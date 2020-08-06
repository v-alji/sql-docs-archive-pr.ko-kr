---
title: 기술 자료 가져오기 및 내보내기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6bd5c4f1acde5d25068ac19a7416069704793345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727348"
---
# <a name="importing-and-exporting-knowledge"></a><span data-ttu-id="51df6-102">기술 자료 가져오기 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="51df6-102">Importing and Exporting Knowledge</span></span>
  <span data-ttu-id="51df6-103">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션에서 직접 기술 자료와 도메인을 만들거나 기술 자료의 정보를 가져오거나 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51df6-103">You can create knowledge bases and domains directly in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application, or you can import knowledge into, or export it from, a knowledge base.</span></span> <span data-ttu-id="51df6-104">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 애플리케이션에서 가져오기 및 내보내기 작업에 데이터 파일을 사용하거나 가져오기 작업에 Excel 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51df6-104">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application, you can use a data file for import and export operations, or an Excel file for import operations.</span></span> <span data-ttu-id="51df6-105">사용되는 데이터 파일은 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )로 만들어 암호화된 파일로서 확장명이 .dqs입니다.</span><span class="sxs-lookup"><span data-stu-id="51df6-105">The data file used is an encrypted file that is created by [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) with a .dqs extension.</span></span> <span data-ttu-id="51df6-106">Microsoft Excel에서 만든 파일은 .xlsx, .xls 또는.csv 확장명을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51df6-106">The files created by Microsoft Excel can have an extension of .xlsx, .xls, or .csv.</span></span> <span data-ttu-id="51df6-107">이러한 작업을 통해 데이터 정리와 일치를 수행하는 데 사용하는 기술 자료를 보다 융통성 있게 작성하고 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51df6-107">These operations give you more flexibility in building and sharing the knowledge that you use to perform data cleansing and matching.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="51df6-108">명령 프롬프트에서 DQSInstaller.exe 파일을 실행하여 *의* 모든 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 기술 자료를 한 번에 DQS 백업 파일(.dqsb)로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51df6-108">You can export *all* the knowledge bases in your [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb) at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="51df6-109">마찬가지로 명령 프롬프트에서 DQSInstaller.exe 파일을 실행하여 DQS 백업 파일(.dqsb)의 *모든* 기술 자료를 한 번에 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51df6-109">Similarly, you can import *all* the knowledge bases from a DQS backup file (.dqsb) to your [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="51df6-110">방법은 DQS 설치 설명서에서 [Dqsinstaller.exe를 사용하여 DQS 기술 자료 내보내기 및 가져오기](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51df6-110">For information about doing so, see [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) in the DQS installation guide.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51df6-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="51df6-111">In This Section</span></span>  
 <span data-ttu-id="51df6-112">다음과 같은 가져오기 및 내보내기 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51df6-112">You can perform the following import and export operations:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51df6-113">기술 자료의 도메인을 .dqs 데이터 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="51df6-113">Export a domain in a knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="51df6-114">.dqs 파일로 도메인 내보내기</span><span class="sxs-lookup"><span data-stu-id="51df6-114">Export a Domain to a .dqs File</span></span>](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|<span data-ttu-id="51df6-115">.dqs 데이터 파일에서 기존의 기술 자료로 도메인 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-115">Import a domain from a .dqs data file into an existing knowledge base</span></span>|[<span data-ttu-id="51df6-116">.dqs 파일에서 도메인 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-116">Import a Domain from a .dqs File</span></span>](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|<span data-ttu-id="51df6-117">전체 기술 자료를 .dqs 데이터 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="51df6-117">Export an entire knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="51df6-118">.dqs 파일로 기술 자료 내보내기</span><span class="sxs-lookup"><span data-stu-id="51df6-118">Export a Knowledge Base to a .dqs File</span></span>](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|<span data-ttu-id="51df6-119">전체 기술 자료를 .dqs 데이터 파일로 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-119">Import an entire knowledge base to a .dqs data file</span></span>|[<span data-ttu-id="51df6-120">.dqs 파일에서 기술 자료 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-120">Import a Knowledge Base from a .dqs File</span></span>](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|<span data-ttu-id="51df6-121">Excel 파일에서 도메인으로 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-121">Import values from an Excel file into a domain</span></span>|[<span data-ttu-id="51df6-122">Excel 파일에서 도메인으로 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-122">Import Values from an Excel File into a Domain</span></span>](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|<span data-ttu-id="51df6-123">Excel 파일에서 기술 자료로 도메인 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-123">Import domains from an Excel file into a knowledge base</span></span>|[<span data-ttu-id="51df6-124">기술 자료 검색 시 Excel 파일에서 도메인 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-124">Import Domains from an Excel File in Knowledge Discovery</span></span>](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|<span data-ttu-id="51df6-125">정리 도중 수집한 정보를 기술 자료로 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-125">Import knowledge gathered during cleansing into a knowledge base</span></span>|[<span data-ttu-id="51df6-126">도메인으로 정리 프로젝트 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="51df6-126">Import Cleansing Project Values into a Domain</span></span>](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="51df6-127">관련 작업</span><span class="sxs-lookup"><span data-stu-id="51df6-127">Related Tasks</span></span>  
  
|<span data-ttu-id="51df6-128">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="51df6-128">Task Description</span></span>|<span data-ttu-id="51df6-129">항목</span><span class="sxs-lookup"><span data-stu-id="51df6-129">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="51df6-130">기술 자료 검색을 실행하고 대화식으로 정보를 관리하여 기술 자료 구축</span><span class="sxs-lookup"><span data-stu-id="51df6-130">Building a knowledge base by running knowledge discovery and interactively managing knowledge</span></span>|[<span data-ttu-id="51df6-131">기술 자료 구축</span><span class="sxs-lookup"><span data-stu-id="51df6-131">Building a Knowledge Base</span></span>](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|<span data-ttu-id="51df6-132">단일 도메인 만들기 및 단일 도메인에 정보 추가</span><span class="sxs-lookup"><span data-stu-id="51df6-132">Creating a single domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="51df6-133">도메인 관리</span><span class="sxs-lookup"><span data-stu-id="51df6-133">Managing a Domain</span></span>](../../2014/data-quality-services/managing-a-domain.md)|  
|<span data-ttu-id="51df6-134">복합 도메인 만들기 및 단일 도메인에 정보 추가</span><span class="sxs-lookup"><span data-stu-id="51df6-134">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="51df6-135">복합 도메인 관리</span><span class="sxs-lookup"><span data-stu-id="51df6-135">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
