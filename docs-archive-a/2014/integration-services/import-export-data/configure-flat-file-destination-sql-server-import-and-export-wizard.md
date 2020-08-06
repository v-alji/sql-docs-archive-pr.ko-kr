---
title: 플랫 파일 대상 구성(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2af8a1653d9a1aef0828aa112a25825ed23b8bf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652937"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a><span data-ttu-id="494dd-102">플랫 파일 대상 구성(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="494dd-102">Configure Flat File Destination (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="494dd-103">**플랫 파일 대상 구성** 페이지를 사용하여 대상 플랫 파일의 서식 옵션을 지정하고 계속하기 전에 결과를 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-103">Use the **Configure Flat File Destination** page to specify formatting options for the destination flat file, and to preview results before continuing.</span></span>  
  
 <span data-ttu-id="494dd-104">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="494dd-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="494dd-105">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 사용 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="494dd-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="494dd-106">SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="494dd-107">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="494dd-108">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="494dd-109">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="494dd-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="494dd-110">옵션</span><span class="sxs-lookup"><span data-stu-id="494dd-110">Options</span></span>  
 <span data-ttu-id="494dd-111">**원본 플랫 파일**</span><span class="sxs-lookup"><span data-stu-id="494dd-111">**Source flat file**</span></span>  
 <span data-ttu-id="494dd-112">대상 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-112">The name of the destination file.</span></span>  
  
 <span data-ttu-id="494dd-113">**행 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="494dd-113">**Row delimiter**</span></span>  
 <span data-ttu-id="494dd-114">행 구분 기호 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-114">Select from the list of delimiters for rows.</span></span>  
  
|<span data-ttu-id="494dd-115">값</span><span class="sxs-lookup"><span data-stu-id="494dd-115">Value</span></span>|<span data-ttu-id="494dd-116">Description</span><span class="sxs-lookup"><span data-stu-id="494dd-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="494dd-117">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="494dd-117">**{CR}{LF}**</span></span>|<span data-ttu-id="494dd-118">행이 캐리지 리턴-줄 바꿈 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-118">The row is delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="494dd-119">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="494dd-119">**{CR}**</span></span>|<span data-ttu-id="494dd-120">행이 캐리지 리턴으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-120">The row is delimited by a carriage return.</span></span>|  
|<span data-ttu-id="494dd-121">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="494dd-121">**{LF}**</span></span>|<span data-ttu-id="494dd-122">행이 줄 바꿈으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-122">The row is delimited by a line feed.</span></span>|  
|<span data-ttu-id="494dd-123">**세미콜론 {;}**</span><span class="sxs-lookup"><span data-stu-id="494dd-123">**Semicolon {;}**</span></span>|<span data-ttu-id="494dd-124">행이 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-124">The row is delimited by a semicolon.</span></span>|  
|<span data-ttu-id="494dd-125">**콜론 {:}**</span><span class="sxs-lookup"><span data-stu-id="494dd-125">**Colon {:}**</span></span>|<span data-ttu-id="494dd-126">행이 콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-126">The row is delimited by a colon.</span></span>|  
|<span data-ttu-id="494dd-127">**쉼표 {,}**</span><span class="sxs-lookup"><span data-stu-id="494dd-127">**Comma {,}**</span></span>|<span data-ttu-id="494dd-128">행이 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-128">The row is delimited by a comma.</span></span>|  
|<span data-ttu-id="494dd-129">**탭 {t}**</span><span class="sxs-lookup"><span data-stu-id="494dd-129">**Tab {t}**</span></span>|<span data-ttu-id="494dd-130">행이 탭으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-130">The row is delimited by a tab.</span></span>|  
|<span data-ttu-id="494dd-131">**세로 막대{&#124;}**</span><span class="sxs-lookup"><span data-stu-id="494dd-131">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="494dd-132">행이 세로 막대로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-132">The row is delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="494dd-133">**열 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="494dd-133">**Column delimiter**</span></span>  
 <span data-ttu-id="494dd-134">열 구분 기호 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-134">Select from the list of delimiters for columns.</span></span>  
  
|<span data-ttu-id="494dd-135">값</span><span class="sxs-lookup"><span data-stu-id="494dd-135">Value</span></span>|<span data-ttu-id="494dd-136">Description</span><span class="sxs-lookup"><span data-stu-id="494dd-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="494dd-137">**{CR}{LF}**</span><span class="sxs-lookup"><span data-stu-id="494dd-137">**{CR}{LF}**</span></span>|<span data-ttu-id="494dd-138">열이 캐리지 리턴-줄 바꿈 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-138">The columns are delimited by a carriage return-line feed combination.</span></span>|  
|<span data-ttu-id="494dd-139">**{CR}**</span><span class="sxs-lookup"><span data-stu-id="494dd-139">**{CR}**</span></span>|<span data-ttu-id="494dd-140">열이 캐리지 리턴으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-140">The columns are delimited by a carriage return.</span></span>|  
|<span data-ttu-id="494dd-141">**{LF}**</span><span class="sxs-lookup"><span data-stu-id="494dd-141">**{LF}**</span></span>|<span data-ttu-id="494dd-142">열이 줄 바꿈으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-142">The columns are delimited by a line feed.</span></span>|  
|<span data-ttu-id="494dd-143">**세미콜론 {;}**</span><span class="sxs-lookup"><span data-stu-id="494dd-143">**Semicolon {;}**</span></span>|<span data-ttu-id="494dd-144">열이 세미콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-144">The columns are delimited by a semicolon.</span></span>|  
|<span data-ttu-id="494dd-145">**콜론 {:}**</span><span class="sxs-lookup"><span data-stu-id="494dd-145">**Colon {:}**</span></span>|<span data-ttu-id="494dd-146">열이 콜론으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-146">The columns are delimited by a colon.</span></span>|  
|<span data-ttu-id="494dd-147">**쉼표 {,}**</span><span class="sxs-lookup"><span data-stu-id="494dd-147">**Comma {,}**</span></span>|<span data-ttu-id="494dd-148">열이 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-148">The columns are delimited by a comma.</span></span>|  
|<span data-ttu-id="494dd-149">**탭 {t}**</span><span class="sxs-lookup"><span data-stu-id="494dd-149">**Tab {t}**</span></span>|<span data-ttu-id="494dd-150">열이 탭으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-150">The columns are delimited by a tab.</span></span>|  
|<span data-ttu-id="494dd-151">**세로 막대{&#124;}**</span><span class="sxs-lookup"><span data-stu-id="494dd-151">**Vertical bar {&#124;}**</span></span>|<span data-ttu-id="494dd-152">열이 세로 막대로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-152">The columns are delimited by a vertical bar.</span></span>|  
  
 <span data-ttu-id="494dd-153">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="494dd-153">**Preview**</span></span>  
 <span data-ttu-id="494dd-154">대상 플랫 파일에 대해 선택한 서식 옵션의 결과를 **데이터 미리 보기** 대화 상자에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-154">View in the **Preview Data** dialog box the results of the selected formatting options for the destination flat file.</span></span>  
  
 <span data-ttu-id="494dd-155">**변환 편집**</span><span class="sxs-lookup"><span data-stu-id="494dd-155">**Edit transform**</span></span>  
 <span data-ttu-id="494dd-156">**열 매핑** 대화 상자를 사용하여 대상 파일의 행을 삭제 또는 추가하고 열을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="494dd-156">Delete rows, append rows, and configure columns in the destination file by using the **Column Mappings** dialog box.</span></span>  
  
  
