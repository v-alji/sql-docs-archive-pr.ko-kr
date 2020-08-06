---
title: 등록된 필터와 단어 분리기 보기 및 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], word breakers
- full-text search [SQL Server], filters
- filters [full-text search]
- word breakers [full-text search]
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79ad7f1f7df15fed21a132bbe253adc7185d8c06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730415"
---
# <a name="view-or-change-registered-filters-and-word-breakers"></a><span data-ttu-id="1c881-102">등록된 필터와 단어 분리기 보기 및 변경</span><span class="sxs-lookup"><span data-stu-id="1c881-102">View or Change Registered Filters and Word Breakers</span></span>
  <span data-ttu-id="1c881-103">시스템에 단어 분리기 또는 필터를 설치하거나 제거한 후 이러한 변경이 자동적으로 서버 인스턴스에 적용되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-103">After any word breakers or filters are installed or uninstalled on a system, the changes do not automatically take effect on server instances.</span></span> <span data-ttu-id="1c881-104">이 항목에서는 현재 등록되어 있는 단어 분리기 또는 필터를 보는 방법과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 새로 설치한 단어 분리기 및 필터를 등록하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-104">This topic describes how to view the currently registered word breaker or filters and how to register newly installed word breakers and filters on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-view-a-list-of-languages-whose-word-breakers-are-currently-registered"></a><span data-ttu-id="1c881-105">현재 등록된 단어 분리기의 언어 목록을 보려면</span><span class="sxs-lookup"><span data-stu-id="1c881-105">To view a list of languages whose word breakers are currently registered</span></span>  
  
1.  <span data-ttu-id="1c881-106">다음과 같이 [sys.fulltext_languages](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) 카탈로그 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-106">Use the [sys.fulltext_languages](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) catalog view, as follows:</span></span>  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### <a name="to-view-a-list-of-the-filters-that-are-currently-registered"></a><span data-ttu-id="1c881-107">현재 등록된 필터의 목록을 보려면</span><span class="sxs-lookup"><span data-stu-id="1c881-107">To view a list of the filters that are currently registered</span></span>  
  
1.  <span data-ttu-id="1c881-108">다음과 같이 [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) 시스템 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-108">Use the [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) system stored procedure, as follows:</span></span>  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### <a name="to-register-newly-installed-word-breakers-and-filters"></a><span data-ttu-id="1c881-109">새로 설치한 단어 분리기 및 필터를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="1c881-109">To register newly installed word breakers and filters</span></span>  
  
1.  <span data-ttu-id="1c881-110">[sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) 시스템 저장 프로시저를 사용하여 다음과 같이 언어 목록을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-110">Use the [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) system stored procedure to update the list of languages, as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### <a name="to-unregister-uninstalled-word-breakers-and-filters"></a><span data-ttu-id="1c881-111">제거한 단어 분리기 및 필터를 등록 취소하려면</span><span class="sxs-lookup"><span data-stu-id="1c881-111">To unregister uninstalled word breakers and filters</span></span>  
  
1.  <span data-ttu-id="1c881-112">**sp_fulltext_service** 를 사용하여 다음과 같이 언어 목록을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-112">Use the **sp_fulltext_service** to update the list of languages, as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  <span data-ttu-id="1c881-113">**sp_fulltext_service** 를 사용하여 다음과 같이 필터 데몬 호스트 프로세스(fdhost.exe)를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-113">Use the **sp_fulltext_service** to restart the filter daemon host processes (fdhost.exe), as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### <a name="to-replace-existing-word-breakers-or-filters-when-installing-new-ones"></a><span data-ttu-id="1c881-114">새로 설치 시 기존 단어 분리기 또는 필터를 교체하려면</span><span class="sxs-lookup"><span data-stu-id="1c881-114">To replace existing word breakers or filters when installing new ones</span></span>  
  
1.  <span data-ttu-id="1c881-115">새로운 단어 분리기 또는 필터가 포함된 DLL 파일을 설치하려고 준비할 때 서버 인스턴스에 설치된 기존 DLL 파일과 다른 파일 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-115">When preparing to install a DLL file that contains new word breakers or filters, verify that it has a different filename from any of the existing DLL files installed on your server instance.</span></span>  
  
2.  <span data-ttu-id="1c881-116">새 DLL 파일을 서버 인스턴스에 대한 표준 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL 파일이 포함된 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-116">Copy the new DLL file into the directory containing the standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL files for the server instance.</span></span> <span data-ttu-id="1c881-117">기본 위치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-117">The default location is:</span></span>  
  
     <span data-ttu-id="1c881-118">C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="1c881-118">C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1c881-119">서명 및 검증을 거친 구성 요소만 로드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-119">We highly recommend that you load only signed and verified components.</span></span> <span data-ttu-id="1c881-120">또한, 최소한의 권한을 가지고 FDHOST Launcher(MSSQLFDLauncher) 서비스를 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-120">Also, we recommend that you run the FDHOST Launcher (MSSQLFDLauncher) Service with the least possible privileges.</span></span>  
  
3.  <span data-ttu-id="1c881-121">새 단어 분리기 또는 필터를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-121">Install the new word breaker or filters.</span></span>  
  
     <span data-ttu-id="1c881-122">**Microsoft Filter Pack IFilter를 설치 및 로드하려면**</span><span class="sxs-lookup"><span data-stu-id="1c881-122">**To install and load Microsoft Filter Pack IFilters**</span></span>  
  
    -   [<span data-ttu-id="1c881-123">SQL Server에 Microsoft Filter Pack IFilter를 등록하는 방법</span><span class="sxs-lookup"><span data-stu-id="1c881-123">How to register Microsoft Filter Pack IFilters with SQL Server</span></span>](https://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  <span data-ttu-id="1c881-124">**sp_fulltext_service** 를 사용하여 새로 설치된 단어 분리기 및 필터를 다음과 같이 서버 인스턴스에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-124">Use **sp_fulltext_service** to load newly installed word breakers and filters in the server instance, as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  <span data-ttu-id="1c881-125">**sp_fulltext_service** 를 사용하여 다음과 같이 언어 목록을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-125">Use **sp_fulltext_service** to update the list of languages, as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  <span data-ttu-id="1c881-126">**sp_fulltext_service** 를 사용하여 다음과 같이 필터 데몬 호스트 프로세스(fdhost.exe)를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1c881-126">Restart the filter daemon host processes (fdhost.exe), using **sp_fulltext_service** as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1c881-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c881-127">See Also</span></span>  
 <span data-ttu-id="1c881-128">[전체 텍스트 필터 데몬 시작 관리자 서비스 계정 설정](set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="1c881-128">[Set the Service Account for the Full-text Filter Daemon Launcher](set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 <span data-ttu-id="1c881-129">[검색 필터 구성 및 관리](configure-and-manage-filters-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="1c881-129">[Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md) </span></span>  
 [<span data-ttu-id="1c881-130">검색을 위해 단어 분리기와 형태소 분석기 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="1c881-130">Configure and Manage Word Breakers and Stemmers for Search</span></span>](configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  
