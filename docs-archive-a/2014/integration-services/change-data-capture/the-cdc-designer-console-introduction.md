---
title: CDC Designer 콘솔 소개 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45298179-4ac1-4723-8b3c-56f5926be40a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 888b111790cf3979e9d08a78502d24880fa034b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646570"
---
# <a name="the-cdc-designer-console-introduction"></a><span data-ttu-id="b4c28-102">CDC Designer 콘솔 소개</span><span class="sxs-lookup"><span data-stu-id="b4c28-102">The CDC Designer Console Introduction</span></span>
  <span data-ttu-id="b4c28-103">이 섹션에서는 Attunity Oracle CDC Designer 설치 절차에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-103">The section describes the installation procedures for the Change Data Capture Designer for Oracle by Attunity.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="b4c28-104">설치</span><span class="sxs-lookup"><span data-stu-id="b4c28-104">Installation</span></span>  
 <span data-ttu-id="b4c28-105">이 섹션에서는 Attunity Oracle CDC Designer 설치 절차에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-105">The section describes the installation procedures for the Change Data Capture Designer for Oracle by Attunity.</span></span> <span data-ttu-id="b4c28-106">CDC Designer 콘솔을 설치 하려면 SQL Server 설치 미디어에서 **AttunityOracleCdcDesigner.msi** 를 수동으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-106">To install the CDC Designer Console, manually run **AttunityOracleCdcDesigner.msi** from the SQL Server installation media.</span></span>  <span data-ttu-id="b4c28-107">X86 및 x 64 용 설치 패키지는 SQL Server 설치 미디어의 \*\*.\Tools\AttunityCDCOracle \\ \*\* 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-107">Installation packages for x86 and x64 are located in **.\Tools\AttunityCDCOracle\\** on the SQL Server installation media.</span></span>  
  
## <a name="supported-windows-environments"></a><span data-ttu-id="b4c28-108">지원되는 Windows 환경</span><span class="sxs-lookup"><span data-stu-id="b4c28-108">Supported Windows Environments</span></span>  
 <span data-ttu-id="b4c28-109">CDC Designer 콘솔은 다음과 같은 Windows 환경에서 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-109">The CDC Designer Console can run in the following Windows environments:</span></span>  
  
-   <span data-ttu-id="b4c28-110">Windows Vista 32비트(x86) 및 64비트(x64) 서비스 팩 2</span><span class="sxs-lookup"><span data-stu-id="b4c28-110">Windows Vista 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
-   <span data-ttu-id="b4c28-111">Windows 7 32비트(x86) 및 64비트(x64)</span><span class="sxs-lookup"><span data-stu-id="b4c28-111">Windows 7 32-bit (x86) and 64-bit (x64)</span></span>  
  
-   <span data-ttu-id="b4c28-112">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b4c28-112">Windows Server 2008 R2</span></span>  
  
-   <span data-ttu-id="b4c28-113">Windows Server 2008 32비트(x86) 및 64비트(x64) 서비스 팩 2</span><span class="sxs-lookup"><span data-stu-id="b4c28-113">Windows Server 2008 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
## <a name="database-prerequisites"></a><span data-ttu-id="b4c28-114">데이터베이스 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b4c28-114">Database Prerequisites</span></span>  
 <span data-ttu-id="b4c28-115">Attunity Oracle CDC Designer 작업은 Oracle 데이터베이스를 사용하여 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-115">To work with the Change Data Capture Designer for Oracle by Attunity, you work with an Oracle database.</span></span> <span data-ttu-id="b4c28-116">Attunity Oracle CDC Designer는 다음과 같은 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-116">The Change Data Capture Designer for Oracle by Attunity supports the following versions:</span></span>  
  
 <span data-ttu-id="b4c28-117">**Oracle 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="b4c28-117">**Oracle Database**</span></span>  
  
-   <span data-ttu-id="b4c28-118">Oracle 데이터베이스 10g 릴리스 2: 10.2.0.1-10.2.0.5(2010년 4월 기준 패치)</span><span class="sxs-lookup"><span data-stu-id="b4c28-118">Oracle Database 10g Release 2: 10.2.0.1-10.2.0.5 (patchset as of April 2010)</span></span>  
  
-   <span data-ttu-id="b4c28-119">Oracle 데이터베이스 11g 릴리스 1: 11.1.0.6-11.1.0.7(2008년 9월 기준 패치)</span><span class="sxs-lookup"><span data-stu-id="b4c28-119">Oracle Database 11g Release 1: 11.1.0.6-11.1.0.7 (patchset as of September 2008)</span></span>  
  
-   <span data-ttu-id="b4c28-120">Oracle 데이터베이스 11g 릴리스 2: 11.2.0.1-11.2.0.3(2011년 9월 기준 패치)</span><span class="sxs-lookup"><span data-stu-id="b4c28-120">Oracle Database 11g Release 2: 11.2.0.1-11.2.0.3 (patchset as of September 2011)</span></span>  
  
 <span data-ttu-id="b4c28-121">**SQL Server 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="b4c28-121">**SQL Server Database**</span></span>  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="b4c28-122">버전</span><span class="sxs-lookup"><span data-stu-id="b4c28-122">edition with support for SQL Server CDC</span></span>  
  
## <a name="software-prerequisites"></a><span data-ttu-id="b4c28-123">소프트웨어 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b4c28-123">Software Prerequisites</span></span>  
 <span data-ttu-id="b4c28-124">다음과 같은 소프트웨어가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-124">The following software is required:</span></span>  
  
-   <span data-ttu-id="b4c28-125">Oracle 10. x 클라이언트</span><span class="sxs-lookup"><span data-stu-id="b4c28-125">Oracle 10.x client</span></span>  
  
-   <span data-ttu-id="b4c28-126">Oracle 11.x 클라이언트</span><span class="sxs-lookup"><span data-stu-id="b4c28-126">Oracle 11.x client</span></span>  
  
 <span data-ttu-id="b4c28-127">**참고**: 설치 된 Oracle CDC Designer 콘솔의 버전에 따라이 소프트웨어의 32 비트 또는 64 비트 버전을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-127">**Note**: You must use the 32-bit or 64-bit version of this software according to the version of the Oracle CDC Designer console installed.</span></span>  
  
 <span data-ttu-id="b4c28-128">Oracle CDC Designer 콘솔은 Oracle ODBC 공급자를 사용하여 원본 Oracle 데이터베이스와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-128">The Oracle CDC Designer Console uses the Oracle ODBC provider to communicate with the source Oracle database.</span></span>  
  
## <a name="running-the-installation-program"></a><span data-ttu-id="b4c28-129">설치 프로그램 실행</span><span class="sxs-lookup"><span data-stu-id="b4c28-129">Running the Installation Program</span></span>  
 <span data-ttu-id="b4c28-130">이 섹션에서는 CDC Designer 콘솔을 설치하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-130">This section describes how to install the CDC Designer Console.</span></span>  
  
 <span data-ttu-id="b4c28-131">**CDC Designer 콘솔을 설치하려면**</span><span class="sxs-lookup"><span data-stu-id="b4c28-131">**To install the CDC Designer Console**</span></span>  
  
 <span data-ttu-id="b4c28-132">CDC Designer 콘솔 설치 키트를 두 번 클릭하고 설치 마법사의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-132">Double-click the CDC Designer Console installation kit and follow the directions in the installation wizard.</span></span>  
  
## <a name="uninstalling-the-cdc-designer-console"></a><span data-ttu-id="b4c28-133">CDC Designer 콘솔 제거</span><span class="sxs-lookup"><span data-stu-id="b4c28-133">Uninstalling the CDC Designer Console</span></span>  
 <span data-ttu-id="b4c28-134">제어판의 프로그램 및 기능을 사용하여 CDC Designer 콘솔을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c28-134">You uninstall the CDC Designer Console using Control Panel, Programs and Features.</span></span>  
  
  
