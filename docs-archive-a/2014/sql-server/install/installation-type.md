---
title: 설치 유형 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 0420c555-7a3b-42b9-8651-0b4f5bcb0008
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bab1b6c912dce64d1269fd79348a2b0b85f7f670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730051"
---
# <a name="installation-type"></a><span data-ttu-id="b72d6-102">설치 유형</span><span class="sxs-lookup"><span data-stu-id="b72d6-102">Installation Type</span></span>
  <span data-ttu-id="b72d6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사의 설치 유형 페이지에서 새로운 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 설치할지, 아니면 기존 인스턴스에 기능을 추가할지 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72d6-103">Use the Installation Type page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify whether to install a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or add features to an existing instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b72d6-104">옵션</span><span class="sxs-lookup"><span data-stu-id="b72d6-104">Options</span></span>  
 <span data-ttu-id="b72d6-105">원하는 항목을 지정하는 라디오 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b72d6-105">Select the radio button that specifies your choice:</span></span>  
  
-   <span data-ttu-id="b72d6-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 새로 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b72d6-106">Perform a new installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="b72d6-107">기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b72d6-107">Add features to an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
     <span data-ttu-id="b72d6-108">기존 인스턴스에 기능을 추가하는 옵션을 선택하는 경우 드롭다운 목록에서 업데이트할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b72d6-108">If you select the option to add features to an existing instance, use the drop-down list to select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to update.</span></span>  
  
 <span data-ttu-id="b72d6-109">[!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 의 준비 이미지에만 SysPrep 지원 기능을 추가할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b72d6-109">You can only add the SysPrep supported features-[!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-to a prepared image of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b72d6-110">SysPrep에서 지원하지 않는 다른 기능은 준비 인스턴스가 완료된 후에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b72d6-110">Other features that are not supported by SysPrep can be added after the prepared instance is completed.</span></span>  
  
 <span data-ttu-id="b72d6-111">**참고:** 이미 설치된 장애 조치(Failover) 클러스터 인스턴스에는 기능을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b72d6-111">**Note** You cannot add features to a failover cluster instance after it is installed.</span></span> <span data-ttu-id="b72d6-112">기존 장애 조치 클러스터에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능을 추가하려면 이 클러스터를 새로 설치하여 별개의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b72d6-112">To add [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features to an existing failover cluster, you must perform a new installation to install a separate instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
