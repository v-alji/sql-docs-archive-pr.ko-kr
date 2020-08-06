---
title: 데이터베이스 복제 설정(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 307d52e24187e35c1c30f609facd13bfad569216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646905"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a><span data-ttu-id="e8be8-102">데이터베이스 복제 설정(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e8be8-102">Enable a Database for Replication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e8be8-103">**sysadmin** 고정 서버 역할의 멤버가 새 게시 마법사로 게시를 만들면 데이터베이스가 복제를 사용할 수 있도록 암시적으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8be8-103">A database is implicitly enabled for replication when a member of the **sysadmin** fixed server role creates a publication with the New Publication Wizard.</span></span> <span data-ttu-id="e8be8-104">**db_owner** 고정 데이터베이스 역할의 멤버가 해당 데이터베이스에 하나 이상의 게시를 만들 수 있도록 **sysadmin** 고정 서버 역할의 멤버는 데이터베이스가 복제를 사용할 수 있도록 명시적으로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8be8-104">A member of the **sysadmin** fixed server role can also enable a database for replication explicitly, so that a member of the **db_owner** fixed database role can create one or more publications in that database.</span></span> <span data-ttu-id="e8be8-105">데이터베이스를 명시적으로 사용하려면 **게시자 속성 - \<Publisher>** 대화 상자의 **게시 데이터베이스** 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e8be8-105">To enable a database explicitly, use the **Publication Databases** page of the **Publisher Properties - \<Publisher>** dialog box.</span></span> <span data-ttu-id="e8be8-106">이 대화 상자에 액세스하는 방법은 [Create a Publication](publish/create-a-publication.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8be8-106">For more information about accessing this dialog box, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
### <a name="to-enable-a-database-for-replication"></a><span data-ttu-id="e8be8-107">데이터베이스 복제를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="e8be8-107">To enable a database for replication</span></span>  
  
1.  <span data-ttu-id="e8be8-108">**게시자 속성 - \<Publisher>** 대화 상자의 **게시 데이터베이스** 페이지에서 복제할 각 데이터베이스에 대해 **트랜잭션** 및/또는 **병합** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e8be8-108">On the **Publication Databases** page of the **Publisher Properties - \<Publisher>** dialog box, select the **Transactional** and/or **Merge** check box for each database you want to replicate.</span></span> <span data-ttu-id="e8be8-109">데이터베이스에서 스냅샷 복제를 설정하려면 **트랜잭션** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e8be8-109">Select **Transactional** to enable the database for snapshot replication.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
