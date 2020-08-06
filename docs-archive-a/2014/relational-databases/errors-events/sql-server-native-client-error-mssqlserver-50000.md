---
title: MSSQLSERVER_50000 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3cc805042bff7259a311ca3f2acf4c26db59381b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732684"
---
# <a name="mssqlserver_50000"></a><span data-ttu-id="c0888-102">MSSQLSERVER_50000</span><span class="sxs-lookup"><span data-stu-id="c0888-102">MSSQLSERVER_50000</span></span>
    
## <a name="details"></a><span data-ttu-id="c0888-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="c0888-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c0888-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="c0888-104">Product Name</span></span>|<span data-ttu-id="c0888-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c0888-105">SQL Server</span></span>|  
|<span data-ttu-id="c0888-106">제품 버전</span><span class="sxs-lookup"><span data-stu-id="c0888-106">Product Version</span></span>|<span data-ttu-id="c0888-107">11.0</span><span class="sxs-lookup"><span data-stu-id="c0888-107">11.0</span></span>|  
|<span data-ttu-id="c0888-108">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="c0888-108">Event ID</span></span>|<span data-ttu-id="c0888-109">50000</span><span class="sxs-lookup"><span data-stu-id="c0888-109">50000</span></span>|  
|<span data-ttu-id="c0888-110">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="c0888-110">Event Source</span></span>|<span data-ttu-id="c0888-111">SETUP</span><span class="sxs-lookup"><span data-stu-id="c0888-111">SETUP</span></span>|  
|<span data-ttu-id="c0888-112">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c0888-112">Component</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0888-113">Native Client</span><span class="sxs-lookup"><span data-stu-id="c0888-113">Native Client</span></span>|  
|<span data-ttu-id="c0888-114">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="c0888-114">Symbolic Name</span></span>||  
|<span data-ttu-id="c0888-115">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="c0888-115">Message Text</span></span>|<span data-ttu-id="c0888-116">'%.\*ls' 파일을 읽는 동안 네트워크가 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="c0888-116">A network error occurred while attempting to read from the file '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c0888-117">설명</span><span class="sxs-lookup"><span data-stu-id="c0888-117">Explanation</span></span>  
 <span data-ttu-id="c0888-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client가 이미 설치되어 있는 컴퓨터에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client를 설치하거나 업데이트하려 했습니다. 기존 설치는 sqlncli.msi에서 이름이 바뀐 MSI 파일에서 설치되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0888-118">An attempt was made to install (or update) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client on a computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is already installed, and where the existing installation was from an MSI file that was renamed from sqlncli.msi.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c0888-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="c0888-119">User Action</span></span>  
 <span data-ttu-id="c0888-120">이 오류를 해결하려면 기존의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 버전을 제거하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0888-120">To resolve this error, uninstall the existing version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="c0888-121">이 오류가 발생하지 않도록 하려면 sqlncli.msi로 이름이 지정되지 않은 MSI 파일에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client를 설치하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="c0888-121">To prevent this error, do not install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client from an MSI file that is not named sqlncli.msi.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="c0888-122">내부 전용</span><span class="sxs-lookup"><span data-stu-id="c0888-122">Internal-Only</span></span>  
  
