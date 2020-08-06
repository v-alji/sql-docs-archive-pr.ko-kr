---
title: 데이터베이스 속성(파일 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.files.f1
ms.assetid: 3c030e51-db82-4b43-b1e5-8547ddd3de87
author: stevestein
ms.author: sstein
ms.openlocfilehash: 955a17857ce0d847fb712473dddd581a072ab83d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728340"
---
# <a name="database-properties-files-page"></a><span data-ttu-id="a747a-102">데이터베이스 속성(파일 페이지)</span><span class="sxs-lookup"><span data-stu-id="a747a-102">Database Properties (Files Page)</span></span>
  <span data-ttu-id="a747a-103">이 페이지를 사용하여 새 데이터베이스를 만들 수 있으며 선택한 데이터베이스의 속성을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-103">Use this page to create a new database, or view or modify properties for the selected database.</span></span> <span data-ttu-id="a747a-104">이 항목은 **새 데이터베이스(일반 페이지)** 와 기존 데이터베이스의 **데이터베이스 속성(파일 페이지)** 에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-104">This topic applies to the **Database Properties (Files Page)** for existing databases, and to the **New Database (General Page)**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a747a-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="a747a-105">UI element list</span></span>  
 <span data-ttu-id="a747a-106">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="a747a-106">**Database name**</span></span>  
 <span data-ttu-id="a747a-107">데이터베이스 이름을 추가하거나 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-107">Add or display the name of the database.</span></span>  
  
 <span data-ttu-id="a747a-108">**소유자**</span><span class="sxs-lookup"><span data-stu-id="a747a-108">**Owner**</span></span>  
 <span data-ttu-id="a747a-109">데이터베이스 소유자를 목록에서 선택하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-109">Specify the owner of the database by selecting from the list.</span></span>  
  
 <span data-ttu-id="a747a-110">**전체 텍스트 인덱싱 사용**</span><span class="sxs-lookup"><span data-stu-id="a747a-110">**Use full-text indexing**</span></span>  
 <span data-ttu-id="a747a-111">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 전체 텍스트 인덱싱이 항상 설정되어 있으므로 이 확인란은 선택된 채로 비활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-111">This check box is checked and disabled because full-text indexing is always enabled in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a747a-112">자세한 내용은 [전체 텍스트 검색](../search/full-text-search.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a747a-112">For more information, see [Full-Text Search](../search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="a747a-113">**데이터베이스 파일**</span><span class="sxs-lookup"><span data-stu-id="a747a-113">**Database Files**</span></span>  
 <span data-ttu-id="a747a-114">관련된 데이터베이스의 데이터베이스 파일을 추가, 보기, 수정 또는 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-114">Add, view, modify, or remove database files for the associated database.</span></span> <span data-ttu-id="a747a-115">데이터베이스 파일의 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-115">Database files have the following properties:</span></span>  
  
 <span data-ttu-id="a747a-116">**논리적 이름**</span><span class="sxs-lookup"><span data-stu-id="a747a-116">**Logical Name**</span></span>  
 <span data-ttu-id="a747a-117">파일 이름을 입력하거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-117">Enter or modify the name of the file.</span></span>  
  
 <span data-ttu-id="a747a-118">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="a747a-118">**File Type**</span></span>  
 <span data-ttu-id="a747a-119">목록에서 파일 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-119">Select the file type from the list.</span></span> <span data-ttu-id="a747a-120">파일 유형은 **데이터**, **로그**또는 **Filestream 데이터**가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-120">The file type can be **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="a747a-121">기존 파일의 파일 유형은 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-121">You cannot modify the file type of an existing file.</span></span>  
  
 <span data-ttu-id="a747a-122">메모리 최적화 파일 그룹에 파일(컨테이너)을 추가하려면 **Filestream 데이터** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-122">Select **Filestream Data** if you are adding files (containers) to a memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="a747a-123">Filestream 데이터 파일 그룹에 파일 (컨테이너)을 추가하려면 FILESTREAM을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-123">To add files (containers) to a Filestream data filegroup, FILESTREAM must be enabled.</span></span> <span data-ttu-id="a747a-124">[서버 속성(고급 페이지)](../../database-engine/configure-windows/server-properties-advanced-page.md) 대화 상자를 사용하여 FILESTREAM을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-124">You can enable FILESTREAM by using the [Server Properties (Advanced Page)](../../database-engine/configure-windows/server-properties-advanced-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="a747a-125">**파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="a747a-125">**Filegroup**</span></span>  
 <span data-ttu-id="a747a-126">목록에서 파일이 속한 파일 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-126">Select the filegroup for the file from the list.</span></span> <span data-ttu-id="a747a-127">기본 파일 그룹은 PRIMARY입니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-127">By default, the filegroup is PRIMARY.</span></span> <span data-ttu-id="a747a-128">**\<new filegroup>** 을 선택하고 **새 파일 그룹** 대화 상자에 파일 그룹에 대한 정보를 입력하여 새 파일 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-128">You can create a new filegroup by selecting **\<new filegroup>** and entering information about the filegroup in the **New Filegroup** dialog box.</span></span> <span data-ttu-id="a747a-129">새 파일 그룹은 **파일 그룹** 페이지에서도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-129">A new filegroup can also be created on the **Filegroup** page.</span></span> <span data-ttu-id="a747a-130">기존 파일의 파일 그룹은 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-130">You cannot modify the filegroup of an existing file.</span></span>  
  
 <span data-ttu-id="a747a-131">메모리 최적화 파일 그룹에 파일(컨테이너)을 추가할 경우 **파일 그룹** 필드에 데이터베이스의 메모리 최적화 파일 그룹 이름이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-131">When adding files (containers) to a memory-optimized filegroup, the **Filegroup** field will be populated with the name of the database's memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="a747a-132">**처음 크기**</span><span class="sxs-lookup"><span data-stu-id="a747a-132">**Initial Size**</span></span>  
 <span data-ttu-id="a747a-133">파일의 처음 크기를 MB 단위로 입력하거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-133">Enter or modify the initial size for the file in megabytes.</span></span> <span data-ttu-id="a747a-134">이 값은 기본적으로 **모델** 데이터베이스의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-134">By default, this is the value of the **model** database.</span></span>  
  
 <span data-ttu-id="a747a-135">FILESTREAM 파일의 경우 이 필드가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-135">This field is not valid for FILESTREAM files.</span></span>  
  
 <span data-ttu-id="a747a-136">메모리 최적화 파일 그룹의 파일에 대해서는 이 필드를 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-136">For files in memory-optimized filegroups, this field cannot be modified.</span></span>  
  
 <span data-ttu-id="a747a-137">**자동 증가**</span><span class="sxs-lookup"><span data-stu-id="a747a-137">**Autogrowth**</span></span>  
 <span data-ttu-id="a747a-138">파일의 자동 증가 속성을 선택하거나 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-138">Select or display the autogrowth properties for the file.</span></span> <span data-ttu-id="a747a-139">이러한 속성은 최대 파일 크기에 도달했을 때 파일의 확장 방법을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-139">These properties control how the file expands when its maximum file size is reached.</span></span> <span data-ttu-id="a747a-140">자동 증가 값을 편집하려면 원하는 파일의 자동 증가 속성 옆에 있는 편집 단추를 클릭하고 **자동 증가 변경** 대화 상자에서 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-140">To edit autogrowth values, click the edit button next to the autogrowth properties for the file that you want, and change the values in the **Change Autogrowth** dialog box.</span></span> <span data-ttu-id="a747a-141">이러한 값은 기본적으로 **모델** 데이터베이스의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-141">By default, these are the values of the **model** database.</span></span>  
  
 <span data-ttu-id="a747a-142">FILESTREAM 파일의 경우 이 필드가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-142">This field is not valid for FILESTREAM files.</span></span>  
  
 <span data-ttu-id="a747a-143">메모리 최적화 파일 그룹의 파일에 대해서는 이 필드가 **제한 없음**이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-143">For files in memory-optimized filegroups, this field should be **Unlimited**.</span></span>  
  
 <span data-ttu-id="a747a-144">**Path**</span><span class="sxs-lookup"><span data-stu-id="a747a-144">**Path**</span></span>  
 <span data-ttu-id="a747a-145">선택한 파일의 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-145">Displays the path of the selected file.</span></span> <span data-ttu-id="a747a-146">새 파일의 경로를 지정하려면 파일 경로 옆에 있는 편집 단추를 클릭하고 대상 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-146">To specify a path for a new file, click the edit button next to the path for the file, and navigate to the destination folder.</span></span> <span data-ttu-id="a747a-147">기존 파일의 경로는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-147">You cannot modify the path of an existing file.</span></span>  
  
 <span data-ttu-id="a747a-148">FILESTREAM 파일의 경우 경로는 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-148">For FILESTREAM files, the path is a folder.</span></span> <span data-ttu-id="a747a-149">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 은 이 폴더에 기본 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-149">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] will create the underlying files in this folder.</span></span>  
  
 <span data-ttu-id="a747a-150">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="a747a-150">**File Name**</span></span>  
 <span data-ttu-id="a747a-151">파일 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-151">Displays the name of the file.</span></span>  
  
 <span data-ttu-id="a747a-152">이 필드는 메모리 최적화 파일 그룹의 파일을 포함한 FILESTREAM 파일에 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-152">This field is not valid for FILESTREAM files, including files in memory-optimized filegroups.</span></span>  
  
 <span data-ttu-id="a747a-153">**추가**</span><span class="sxs-lookup"><span data-stu-id="a747a-153">**Add**</span></span>  
 <span data-ttu-id="a747a-154">데이터베이스에 새 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-154">Add a new file to the database.</span></span>  
  
 <span data-ttu-id="a747a-155">**제거**</span><span class="sxs-lookup"><span data-stu-id="a747a-155">**Remove**</span></span>  
 <span data-ttu-id="a747a-156">선택한 파일을 데이터베이스에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-156">Delete the selected file from the database.</span></span> <span data-ttu-id="a747a-157">파일이 비어 있지 않으면 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-157">A file cannot be removed unless it is empty.</span></span> <span data-ttu-id="a747a-158">주 데이터 파일과 로그 파일은 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a747a-158">The primary data file and log file cannot be removed.</span></span>  
  
 <span data-ttu-id="a747a-159">파일에 대한 자세한 내용은 [Database Files and Filegroups](database-files-and-filegroups.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a747a-159">For information about files, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a747a-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a747a-160">See Also</span></span>  
 <span data-ttu-id="a747a-161">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a747a-161">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="a747a-162">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a747a-162">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
