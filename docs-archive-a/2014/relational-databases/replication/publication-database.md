---
title: 게시 데이터베이스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 511e5f2e2caa934313ba96fb3dbc4cadddace968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646345"
---
# <a name="publication-database"></a><span data-ttu-id="91f59-102">게시 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="91f59-102">Publication Database</span></span>
  <span data-ttu-id="91f59-103">게시 데이터베이스는 복제될 데이터 및 데이터베이스 개체의 원본인 게시자에 있는 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="91f59-103">The publication database is the database on the Publisher that is the source of data and database objects to be replicated.</span></span> <span data-ttu-id="91f59-104">복제에 사용할 각 게시 데이터베이스는 활성화되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91f59-104">Each publication database used in replication must be enabled.</span></span> <span data-ttu-id="91f59-105">데이터베이스는 **sysadmin** 고정 서버 역할의 멤버가 다음과 같은 작업을 수행할 때 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="91f59-105">The database is enabled when a member of the **sysadmin** fixed server role:</span></span>  
  
-   <span data-ttu-id="91f59-106">새 게시 마법사를 사용하여 데이터베이스에 게시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91f59-106">Creates a publication on that database using the New Publication Wizard.</span></span>  
  
-   <span data-ttu-id="91f59-107">**게시자 속성** 대화 상자에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91f59-107">Selects the database in the **Publisher Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="91f59-108">**sp_replicationdboption** 을 실행하여 **publish** (스냅샷 또는 트랜잭션 게시의 경우) 또는 **merge publish** (병합 게시의 경우) 옵션을 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f59-108">Executes **sp_replicationdboption** and sets the option **publish** (for snapshot or transactional publications) or **merge publish** (for merge publications) to **True**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="91f59-109">옵션</span><span class="sxs-lookup"><span data-stu-id="91f59-109">Options</span></span>  
 <span data-ttu-id="91f59-110">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="91f59-110">**Databases**</span></span>  
 <span data-ttu-id="91f59-111">게시할 데이터 및 데이터베이스 개체를 포함하는 데이터베이스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91f59-111">Select the name of the database that contains the data and database objects that you want to publish.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f59-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91f59-112">See Also</span></span>  
 <span data-ttu-id="91f59-113">[데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="91f59-113">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="91f59-114">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="91f59-114">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="91f59-115">[배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="91f59-115">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="91f59-116">sp_replicationdboption&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="91f59-116">sp_replicationdboption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  
