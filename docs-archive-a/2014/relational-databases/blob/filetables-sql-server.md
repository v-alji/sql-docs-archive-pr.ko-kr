---
title: Filetable(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 07/06/2016
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], overview
- FileTables [SQL Server]
- FileTable [SQL Server], see FileTables [SQL Server]
- FileTable [SQL Server]
ms.assetid: a57b629c-e9ed-48fd-9a48-ed3787d80c8f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c0a38f0e947b0c4f68a49e13a40071f6a30cd07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740060"
---
# <a name="filetables-sql-server"></a><span data-ttu-id="5e0a8-102">FileTable(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5e0a8-102">FileTables (SQL Server)</span></span>
  <span data-ttu-id="5e0a8-103">FileTable 기능은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장된 파일 데이터에 대해 Windows 파일 네임스페이스 및 Windows 애플리케이션과의 호환성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-103">The FileTable feature brings support for the Windows file namespace and compatibility with Windows applications to the file data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5e0a8-104">FileTable을 통해 애플리케이션이 해당 스토리지 및 데이터 관리 구성 요소를 통합할 수 있으며, 구조화되지 않은 데이터 및 메타데이터에 대한 통합 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스(전체 텍스트 검색 및 의미 체계 검색 포함)가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-104">FileTable lets an application integrate its storage and data management components, and provides integrated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services - including full-text search and semantic search - over unstructured data and metadata.</span></span>  
  
 <span data-ttu-id="5e0a8-105">즉, 파일 및 문서를 FileTable이라는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 특수 테이블에 저장할 수 있지만, Windows 애플리케이션에서 해당 파일 및 문서에 액세스할 때는 파일 시스템에 저장된 파일 및 문서에 액세스할 때와 같은 방식으로 처리됩니다. 클라이언트 애플리케이션을 변경할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-105">In other words, you can store files and documents in special tables in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] called FileTables, but access them from Windows applications as if they were stored in the file system, without making any changes to your client applications.</span></span>  
  
 <span data-ttu-id="5e0a8-106">FileTable은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] FILESTREAM 기술을 기반으로 구축된 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-106">The FileTable feature builds on top of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] FILESTREAM technology.</span></span> <span data-ttu-id="5e0a8-107">FILESTREAM에 대한 자세한 내용은 [FILESTREAM&#40;SQL Server&#41;](filestream-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-107">To learn more about FILESTREAM, see [FILESTREAM &#40;SQL Server&#41;](filestream-sql-server.md).</span></span>  
  
##  <a name="benefits-of-the-filetable-feature"></a><a name="Goals"></a> <span data-ttu-id="5e0a8-108">FileTable 기능의 이점</span><span class="sxs-lookup"><span data-stu-id="5e0a8-108">Benefits of the FileTable Feature</span></span>  
 <span data-ttu-id="5e0a8-109">FileTable 기능의 목적은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-109">The goals of the FileTable feature include the following:</span></span>  
  
-   <span data-ttu-id="5e0a8-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 내에 저장된 파일 데이터에 대한 Windows API 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-110">Windows API compatibility for file data stored within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="5e0a8-111">Windows API 호환성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-111">Windows API compatibility includes the following:</span></span>  
  
    -   <span data-ttu-id="5e0a8-112">FILESTREAM 데이터에 비트랜잭션 스트리밍 방식으로 액세스하여 해당 데이터를 현재 위치에서 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-112">Non-transactional streaming access and in-place updates to FILESTREAM data.</span></span>  
  
    -   <span data-ttu-id="5e0a8-113">디렉터리 및 파일의 계층 네임스페이스가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-113">A hierarchical namespace of directories and files.</span></span>  
  
    -   <span data-ttu-id="5e0a8-114">파일을 만든 날짜와 수정한 날짜 같은 파일 특성의 스토리지가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-114">Storage of file attributes, such as created date and modified date.</span></span>  
  
    -   <span data-ttu-id="5e0a8-115">Windows 파일 및 디렉터리 관리 API가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-115">Support for Windows file and directory management APIs.</span></span>  
  
-   <span data-ttu-id="5e0a8-116">FILESTREAM 및 파일 특성 데이터를 통해 관리 도구, 서비스 및 관계형 쿼리 기능을 비롯한 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능과의 호환성이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-116">Compatibility with other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features including management tools, services, and relational query capabilities over FILESTREAM and file attribute data.</span></span>  
  
 <span data-ttu-id="5e0a8-117">파일 서버에 현재 파일로 존재하는 구조화되지 않은 데이터를 스토리지하고 관리하는 데 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하려면 여러 가지 문제를 해결해야 했지만 FileTable을 사용하면 이러한 문제가 상당히 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-117">Thus FileTables remove a significant barrier to the use of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the storage and management of unstructured data that is currently residing as files on file servers.</span></span> <span data-ttu-id="5e0a8-118">기업에서는 파일 서버의 데이터를 FileTable로 이동하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 제공하는 통합된 관리 기능 및 서비스를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-118">Enterprises can move this data from file servers into FileTables to take advantage of integrated administration and services provided by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5e0a8-119">동시에 해당 데이터를 파일 시스템의 파일로 표시하는 기존의 Windows 애플리케이션을 위해 Windows 애플리케이션 호환성을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-119">At the same time, they can maintain Windows application compatibility for their existing Windows applications that see this data as files in the file system.</span></span>  
    
##  <a name="what-is-a-filetable"></a><a name="Description"></a> <span data-ttu-id="5e0a8-120">FileTable 정의</span><span class="sxs-lookup"><span data-stu-id="5e0a8-120">What Is a FileTable?</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5e0a8-121">데이터베이스에 파일 및 디렉터리를 스토리지해야 하며 Windows API 호환성과 비트랜잭션 액세스가 필요한 애플리케이션을 위해 **FileTable**이라는 특수한 **파일 테이블**을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-121">provides a special **table of files**, also referred to as a **FileTable**, for applications that require file and directory storage in the database, with Windows API compatibility and non-transactional access.</span></span> <span data-ttu-id="5e0a8-122">FileTable은 미리 정의된 스키마를 사용하여 파일 및 디렉터리 계층 구조 정보와 파일 특성은 물론 FILESTREAM 데이터도 저장하는 특수한 사용자 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-122">A FileTable is a specialized user table with a pre-defined schema that stores FILESTREAM data, as well as file and directory hierarchy information and file attributes.</span></span>  
  
 <span data-ttu-id="5e0a8-123">FileTable에서는 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-123">A FileTable provides the following functionality:</span></span>  
  
-   <span data-ttu-id="5e0a8-124">FileTable은 디렉터리 및 파일의 계층 구조를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-124">A FileTable represents a hierarchy of directories and files.</span></span> <span data-ttu-id="5e0a8-125">FileTable은 이 계층 구조의 모든 노드(계층 구조에 포함된 디렉터리와 파일의 노드)와 관련된 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-125">It stores data related to all the nodes in that hierarchy, for both directories and the files they contain.</span></span> <span data-ttu-id="5e0a8-126">이 계층 구조는 FileTable을 만들 때 지정하는 루트 디렉터리에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-126">This hierarchy starts from a root directory that you specify when you create the FileTable.</span></span>  
  
-   <span data-ttu-id="5e0a8-127">FileTable의 각 행은 파일 또는 디렉터리 하나를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-127">Every row in a FileTable represents a file or a directory.</span></span>  
  
-   <span data-ttu-id="5e0a8-128">각 행에는 다음 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-128">Every row contains the following items.</span></span> <span data-ttu-id="5e0a8-129">FileTable의 스키마에 대한 자세한 내용은 [FileTable Schema](filetable-schema.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-129">For more information about the schema of a FileTable, see [FileTable Schema](filetable-schema.md).</span></span>  
  
    -   <span data-ttu-id="5e0a8-130">스트림 데이터의**file_stream** 열 및 **stream_id** (GUID) 식별자</span><span class="sxs-lookup"><span data-stu-id="5e0a8-130">A**file_stream** column for stream data and a **stream_id** (GUID) identifier.</span></span> <span data-ttu-id="5e0a8-131">(디렉터리의 경우 **file_stream** 열은 NULL입니다.)</span><span class="sxs-lookup"><span data-stu-id="5e0a8-131">(The **file_stream** column is NULL for a directory.)</span></span>  
  
    -   <span data-ttu-id="5e0a8-132">파일 및 디렉터리 계층 구조를 나타내고 유지 관리하기 위한 **path_locator** 및 **parent_path_locator** 열</span><span class="sxs-lookup"><span data-stu-id="5e0a8-132">Both **path_locator** and **parent_path_locator** columns for representing and maintaining the file and directory hierarchy.</span></span>  
  
    -   <span data-ttu-id="5e0a8-133">파일 I/O API에 유용한 파일 작성 날짜 및 수정 날짜 같은 10개의 파일 특성</span><span class="sxs-lookup"><span data-stu-id="5e0a8-133">10 file attributes such as created date and modified date that are useful with file I/O APIs.</span></span>  
  
    -   <span data-ttu-id="5e0a8-134">파일 및 문서에 대한 전체 텍스트 검색과 의미 체계 검색을 지원하는 Type 열</span><span class="sxs-lookup"><span data-stu-id="5e0a8-134">A type column that supports full-text search and semantic search over files and documents.</span></span>  
  
-   <span data-ttu-id="5e0a8-135">FileTable은 특정 시스템 정의 제약 조건 및 트리거를 적용하여 파일 네임스페이스의 의미 체계를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-135">A FileTable enforces certain system-defined constraints and triggers to maintain file namespace semantics.</span></span>  
  
-   <span data-ttu-id="5e0a8-136">데이터베이스가 비트랜잭션 액세스용으로 구성된 경우 FileTable에 표시되는 파일 및 디렉터리 계층 구조는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스용으로 구성된 FILESTREAM 공유를 통해 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-136">When the database is configured for non-transactional access, the file and directory hierarchy represented in the FileTable is exposed under the FILESTREAM share configured for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="5e0a8-137">Windows 애플리케이션에서는 이를 통해 파일 시스템에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-137">This provides file system access for Windows applications.</span></span>  
  
 <span data-ttu-id="5e0a8-138">FileTable에는 다음과 같은 특징도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-138">Some additional characteristics of FileTables include the following:</span></span>  
  
-   <span data-ttu-id="5e0a8-139">FileTable에 저장된 파일 및 디렉터리 데이터는 Windows API 기반 애플리케이션의 비트랜잭션 파일 액세스를 위한 Windows 공유를 통해 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-139">The file and directory data stored in a FileTable is exposed through a Windows share for non-transactional file access for Windows API based applications.</span></span> <span data-ttu-id="5e0a8-140">Windows 애플리케이션에서는 이러한 공유를 해당 애플리케이션의 파일 및 디렉터리를 포함하는 일반적인 공유와 동일하게 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-140">For a Windows application, this looks like a normal share with its files and directories.</span></span> <span data-ttu-id="5e0a8-141">애플리케이션에서는 풍부한 Windows API를 사용하여 이 공유에 있는 파일 및 디렉터리를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-141">Applications can use a rich set of Windows APIs to manage the files and directories under this share.</span></span>  
  
-   <span data-ttu-id="5e0a8-142">공유를 통해 표시되는 디렉터리 계층 구조는 FileTable 내에서 유지 관리되는 완전히 논리적인 디렉터리 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-142">The directory hierarchy surfaced through the share is a purely logical directory structure that is maintained within the FileTable.</span></span>  
  
-   <span data-ttu-id="5e0a8-143">Windows 공유를 통해 파일 또는 디렉터리를 만들거나 변경하려고 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소에서 해당 호출을 가로채어 FileTable에 있는 해당 관계형 데이터에 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-143">Calls to create or change a file or directory through the Windows share are intercepted by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component and reflected in the corresponding relational data in the FileTable.</span></span>  
  
-   <span data-ttu-id="5e0a8-144">Windows API 작업은 본질적으로 비트랜잭션이며 사용자 트랜잭션과 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-144">Windows API operations are non-transactional in nature, and are not associated with user transactions.</span></span> <span data-ttu-id="5e0a8-145">그러나 일반 테이블에 있는 FILESTREAM 열의 경우와 마찬가지로 FileTable에 저장된 FILESTREAM 데이터에 대한 트랜잭션 액세스도 완전히 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-145">However, transactional access to FILESTREAM data stored in a FileTable is fully supported, as is the case for any FILESTREAM column in a regular table.</span></span>  
  
-   <span data-ttu-id="5e0a8-146">일반적인 [!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스를 통해 FileTable을 쿼리하고 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-146">FileTables can also be queried and updated through normal [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="5e0a8-147">또한 FileTable은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리 도구나 백업 등의 기능과 통합되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-147">They are also integrated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management tools, and features such as backup.</span></span>  
  
  
##  <a name="additional-considerations-for-using-filetables"></a><a name="additional"></a> <span data-ttu-id="5e0a8-148">FileTable 사용에 대한 추가 고려 사항</span><span class="sxs-lookup"><span data-stu-id="5e0a8-148">Additional Considerations for Using FileTables</span></span>  
  
###  <a name="administrative-considerations"></a><a name="DBA"></a> <span data-ttu-id="5e0a8-149">관리 고려 사항</span><span class="sxs-lookup"><span data-stu-id="5e0a8-149">Administrative Considerations</span></span>  
 <span data-ttu-id="5e0a8-150">**FILESTREAM 및 FileTable 정보**</span><span class="sxs-lookup"><span data-stu-id="5e0a8-150">**About FILESTREAM and FileTables**</span></span>  
  
-   <span data-ttu-id="5e0a8-151">FileTable은 FILESTREAM과는 별도로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-151">You configure FileTables separately from FILESTREAM.</span></span> <span data-ttu-id="5e0a8-152">따라서 비트랜잭션 액세스를 사용하도록 설정하거나 FileTable을 만들지 않고도 FILESTREAM 기능을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-152">Therefore you can continue to use the FILESTREAM feature without enabling non-transactional access or creating FileTables.</span></span>  
  
-   <span data-ttu-id="5e0a8-153">FileTable을 통하지 않고 FILESTREAM 데이터에 비트랜잭션 방식으로 액세스할 수 있는 방법은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-153">There is no non-transactional access to FILESTREAM data except through FileTables.</span></span> <span data-ttu-id="5e0a8-154">따라서 비트랜잭션 액세스를 사용하도록 설정해도 기존 FILESTREAM 열 및 애플리케이션의 동작에는 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-154">Therefore, when you enable non-transactional access, the behavior of existing FILESTREAM columns and applications is not affected.</span></span>  
  
 <span data-ttu-id="5e0a8-155">**FileTable 및 비트랜잭션 액세스 정보**</span><span class="sxs-lookup"><span data-stu-id="5e0a8-155">**About FileTables and non-transactional access**</span></span>  
  
-   <span data-ttu-id="5e0a8-156">데이터베이스 수준에서 비트랜잭션 액세스를 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-156">You can enable or disable non-transactional access at the database level.</span></span>  
  
-   <span data-ttu-id="5e0a8-157">데이터베이스 수준에서 비트랜잭션 액세스를 해제하거나 읽기 전용 또는 모든 읽기/쓰기 액세스를 허용하도록 설정하는 방법으로 비트랜잭션 액세스를 구성하거나 세부적으로 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-157">You can configure or fine-tune non-transactional access at the database level by turning it off, or by enabling read only or full read/write access.</span></span>  
  
  
###  <a name="filetables-do-not-support-memory-mapped-files"></a><a name="memory"></a> <span data-ttu-id="5e0a8-158">FileTable은 메모리 매핑된 파일을 지원하지 않음</span><span class="sxs-lookup"><span data-stu-id="5e0a8-158">FileTables Do Not Support Memory-Mapped Files</span></span>  
 <span data-ttu-id="5e0a8-159">FileTable은 메모리 매핑된 파일을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-159">FileTables do not support memory-mapped files.</span></span> <span data-ttu-id="5e0a8-160">메모장과 그림판이 메모리 매핑된 파일을 사용하는 애플리케이션 중 가장 일반적인 두 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-160">Notepad and Paint are two common examples of applications that use memory-mapped files.</span></span> <span data-ttu-id="5e0a8-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 같은 컴퓨터에서 이러한 애플리케이션을 사용하여 FileTable에 저장된 파일을 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-161">You cannot use these applications on the same computer as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to open files that are stored in a FileTable.</span></span> <span data-ttu-id="5e0a8-162">하지만 원격 컴퓨터 환경에서는 메모리 매핑된 기능을 사용하지 않으므로 원격 컴퓨터에서 이러한 애플리케이션을 사용하여 FileTable에 저장된 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-162">However you can use these applications from a remote computer to open files that are stored in a FileTable, because in these circumstances the memory-mapping feature is not used.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="5e0a8-163">관련 작업</span><span class="sxs-lookup"><span data-stu-id="5e0a8-163">Related Tasks</span></span>  
 [<span data-ttu-id="5e0a8-164">FileTable의 필수 구성 요소를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="5e0a8-164">Enable the Prerequisites for FileTable</span></span>](enable-the-prerequisites-for-filetable.md)  
 <span data-ttu-id="5e0a8-165">FileTable을 만들고 사용하기 위한 필수 구성 요소를 사용하도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-165">Describes how to enable the prerequisites for creating and using FileTables.</span></span>  
  
 [<span data-ttu-id="5e0a8-166">FileTable 만들기, 변경 및 삭제</span><span class="sxs-lookup"><span data-stu-id="5e0a8-166">Create, Alter, and Drop FileTables</span></span>](create-alter-and-drop-filetables.md)  
 <span data-ttu-id="5e0a8-167">새 FileTable을 만들거나 기존 FileTable을 변경 또는 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-167">Describes how to create a new FileTable, or alter or drop an existing FileTable.</span></span>  
  
 [<span data-ttu-id="5e0a8-168">FileTable로 파일 로드</span><span class="sxs-lookup"><span data-stu-id="5e0a8-168">Load Files into FileTables</span></span>](load-files-into-filetables.md)  
 <span data-ttu-id="5e0a8-169">파일을 FileTable로 로드 또는 마이그레이션하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-169">Describes how to load or migrate files into FileTables.</span></span>  
  
 [<span data-ttu-id="5e0a8-170">FileTable에서 디렉터리 및 경로 작업</span><span class="sxs-lookup"><span data-stu-id="5e0a8-170">Work with Directories and Paths in FileTables</span></span>](work-with-directories-and-paths-in-filetables.md)  
 <span data-ttu-id="5e0a8-171">파일이 FileTable에 저장되는 디렉터리 구조에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-171">Describes the directory structure in which the files are stored in FileTables.</span></span>  
  
 [<span data-ttu-id="5e0a8-172">Transact-SQL을 사용하여 FileTable 액세스</span><span class="sxs-lookup"><span data-stu-id="5e0a8-172">Access FileTables with Transact-SQL</span></span>](access-filetables-with-transact-sql.md)  
 <span data-ttu-id="5e0a8-173">FileTable에서 Transact-SQL DML(데이터 조작 언어) 명령이 작동하는 방식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-173">Describes how Transact-SQL data manipulation language (DML) commands work with FileTables.</span></span>  
  
 [<span data-ttu-id="5e0a8-174">파일 입/출력 API를 사용하여 FileTable 액세스</span><span class="sxs-lookup"><span data-stu-id="5e0a8-174">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
 <span data-ttu-id="5e0a8-175">FileTable에서 파일 시스템 I/O가 작동하는 방식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-175">Describes how file system I/O works on a FileTable.</span></span>  
  
 [<span data-ttu-id="5e0a8-176">FileTable 관리</span><span class="sxs-lookup"><span data-stu-id="5e0a8-176">Manage FileTables</span></span>](manage-filetables.md)  
 <span data-ttu-id="5e0a8-177">FileTable을 관리하는 데 사용되는 일반적인 관리 태스크에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-177">Describes common administrative tasks for managing FileTables.</span></span>  
  
  
##  <a name="related-content"></a><a name="relcontent"></a> <span data-ttu-id="5e0a8-178">관련 내용</span><span class="sxs-lookup"><span data-stu-id="5e0a8-178">Related Content</span></span>  
 [<span data-ttu-id="5e0a8-179">FileTable 스키마</span><span class="sxs-lookup"><span data-stu-id="5e0a8-179">FileTable Schema</span></span>](filetable-schema.md)  
 <span data-ttu-id="5e0a8-180">FileTable의 미리 정의된 고정 스키마에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-180">Describes the pre-defined and fixed schema of a FileTable.</span></span>  
  
 [<span data-ttu-id="5e0a8-181">FileTable과 기타 SQL Server 기능 간 호환성</span><span class="sxs-lookup"><span data-stu-id="5e0a8-181">FileTable Compatibility with Other SQL Server Features</span></span>](filetable-compatibility-with-other-sql-server-features.md)  
 <span data-ttu-id="5e0a8-182">FileTable이 SQL Server의 다른 기능과 함께 작동하는 방식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-182">Describes how FileTables work with other features of SQL Server.</span></span>  
  
 [<span data-ttu-id="5e0a8-183">FileTable DDL, 함수, 저장 프로시저 및 뷰</span><span class="sxs-lookup"><span data-stu-id="5e0a8-183">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
 <span data-ttu-id="5e0a8-184">FileTable 기능을 지원하기 위해 추가되거나 변경된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 개체를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0a8-184">Lists the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects that have been added or changed to support the FileTable feature.</span></span>  
  
 
  
