---
title: 개체 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7b20d1eee3e48c5531b6b788e125b943f7606d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638528"
---
# <a name="delete-objects"></a><span data-ttu-id="22582-102">개체 삭제</span><span class="sxs-lookup"><span data-stu-id="22582-102">Delete Objects</span></span>
  <span data-ttu-id="22582-103">이 대화 상자를 사용하여 데이터베이스나 데이터베이스 개체를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22582-103">Use this dialog box to delete a database or database object.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="22582-104">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="22582-104">UI element list</span></span>  
 <span data-ttu-id="22582-105">**삭제할 개체**</span><span class="sxs-lookup"><span data-stu-id="22582-105">**Object to be deleted**</span></span>  
 <span data-ttu-id="22582-106">삭제하려고 하는 개체의 이름, 유형, 소유자 및 상태와 실행하는 동안 발생한 오류에 대한 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="22582-106">Displays the names, types, owners, and status of the objects that are about to be deleted, as well as any messages about errors during execution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22582-107">데이터베이스에서 **삭제** 를 실행하는 것은 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 DROP DATABASE를 실행하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="22582-107">Running **Delete** on a database is equivalent to issuing DROP DATABASE in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="22582-108">**종속성 표시**</span><span class="sxs-lookup"><span data-stu-id="22582-108">**Show Dependencies**</span></span>  
 <span data-ttu-id="22582-109">현재 선택한 개체에 종속된 개체와 현재 개체가 종속된 개체(상향 및 하향 종속성)를 모두 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22582-109">Click to display both the objects that are dependent on the currently selected object and objects that the current object is dependent on (upward and downward dependency).</span></span> <span data-ttu-id="22582-110">**종속성 표시** 대화 상자에 표시된 정보는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="22582-110">The information displayed in the **Show Dependencies** dialog box is read-only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22582-111">**종속성 표시** 단추는 모든 유형의 데이터베이스 개체에 대해 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22582-111">The **Show Dependencies** button does not appear for all types of database objects.</span></span> <span data-ttu-id="22582-112">**종속성 표시** 단추를 사용할 수 없을 때 종속성을 보려면 개체 탐색기에서 개체를 마우스 오른쪽 단추로 클릭한 다음 **종속성 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="22582-112">To view dependencies when the **Show Dependencies** button is not available, right-click the object in Object Explorer, and then click **View Dependencies**.</span></span>  
  
 <span data-ttu-id="22582-113">**백업 삭제 및 데이터베이스에 대한 기록 정보 복원**</span><span class="sxs-lookup"><span data-stu-id="22582-113">**Delete backup and restore history information for databases**</span></span>  
 <span data-ttu-id="22582-114">데이터베이스가 삭제될 때만 나타나는 이 확인란을 선택하면 **msdb** 데이터베이스에서 주제 데이터베이스에 대한 백업 및 복원 기록이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="22582-114">Only appears when a database is deleted, this check box causes the backup and restore history for the subject database to be deleted from the **msdb** database.</span></span>  
  
 <span data-ttu-id="22582-115">**기존 연결 닫기**</span><span class="sxs-lookup"><span data-stu-id="22582-115">**Close existing connections**</span></span>  
 <span data-ttu-id="22582-116">데이터베이스가 삭제될 때만 나타나는 이 확인란을 선택하면 주제 데이터베이스에 대한 연결이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="22582-116">Only appears when a database is deleted, this check box terminates connections to the subject database.</span></span>  
  
  
